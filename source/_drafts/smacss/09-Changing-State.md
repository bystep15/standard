# Changing State

[原文](https://smacss.com/book/state)

You’ve got a Photoshop document open in front of you and you have been told to turn it into the magic that is HTML and CSS (with maybe a little JavaScript thrown in for good measure).

It may seem straightforward to start mapping things directly from the composition to the code. However, various components on your page are likely to need to be represented in various states. There is the default state that something should appear in and then what it should look like when the state changes.

## What is a state change?

State changes are represented in one of three ways:

1. class name
2. pseudo-class
3. media query

A **class name** change happens with JavaScript. Via some interaction, be it moving the mouse around, hitting something on the keyboard, or some other event occurring. An element gets a new class applied and then the visual appearance changes.

A **pseudo-class** change is done via any number of pseudo-classes, and there are a lot. In these cases, we no longer have to rely on JavaScript to describe the state change. Pseudo-classes are still limited in that we can only style changes to elements that are descendants or siblings of the element in which the pseudo-class applies. Otherwise, we are back to using JavaScript.

Lastly, **media queries** describe how things should be styled under defined criteria, such as different viewport sizes.

With a module-based system, it is important to consider state-based design as applied to each of the modules. When you actively ask yourself, “what is the default state,” then you’ll find yourself thinking proactively about progressive enhancement. It also can have you approaching issues slightly differently.

## Change via Class Name

For the most part, class name changes are straightforward. These are applied to elements that take on a different state. For example, a user clicks on a disclosure icon to show and hide an element on the page.



JavaScript changing state via class name

```
// with jQuery
$('.btn-close').click(function(){ 
    $(this).parents('.dialog').addClass('is-hidden');        
})
```



The jQuery example adds a click event handler to every element with the `btn-close` class name. When the user clicks on the button, it takes the event source and works up the DOM tree to find the ancestor element with the class of `dialog` on it. Then it applies the `is-hidden` state class.

Other times, a state change has a greater impact.

A common interface design pattern is that of a button being pressed and displaying a menu. In this case, the menu changes to a pressed state and the menu changes to a visible state. What options do we have for handling this change? It depends heavily on your HTML structure. For example, at Yahoo!, menus get loaded at request time and are, therefore, inserted at the top of the DOM. We had used a naming convention to hook the two together.



Button and menu in separate parts of the same document

```
<div id="content">
   <div class="toolbar">
      <button id="btn-new" class="btn" data-action="menu">New</button>
   </div>
</div>
<div id="menu-new" class="menu">
   <ul> ... </ul>
</div>
```



The data-action tied into a JavaScript click call that said, "hey, you want to load a menu." It would take the button ID and find the menu that matched. This is how it might work with jQuery:



Loading Menu with jQuery

```
// bind a click handler to the button
$('#btn-new').click(function(){
    // wrap the clicked button in jQuery
    var el = $(this); 

    // change the state of the button
    el.addClass('is-pressed');

    // find the menu by stripping btn- and
    // adding it to menu selector
    $('#menu-' + el.id.substr(4)).removeClass('is-hidden');
});
```



As this illustrates, the state change for a single item is modified on two different items in two different places via JavaScript.

But what if the menu actually resided right next to the button?



Button and menu in the same part of the document

```
<div id="content">
   <div class="toolbar">
      <button id="btn-new" class="btn" data-action="menu">New</button>
      <div id="menu-new" class="menu">
          <ul> ... </ul>
      </div>
   </div>
</div>
```



The previous code would work exactly the same and could definitely stay the same. However, we have alternatives. Your first instinct might be to add a class to a parent element and style the button and menu from there.



Adding a class to parent element to style child elements

```
<div id="content">
   <div class="toolbar is-active">
      <button id="btn-new" class="btn" data-action="menu">New</button>
      <div id="menu-new" class="menu">
          <ul> ... </ul>
      </div>
   </div>
</div>

/* CSS for styling */

.is-active .btn { color: #000; }
.is-active .menu { display: block; }
```



The problem with this approach is that this HTML structure is now tied together. There must be a containing element. The menu and button must exist within that containing element. Let's hope we don't need to add any more buttons into that toolbar!

Another approach to this is to apply the active class to the button as we did before and use the sibling selector to activate the menu.



Activating the menu with a sibling selector

```
<div id="content">
   <div class="toolbar">
      <button id="btn-new" class="btn is-active" data-action="menu">New</button>
      <div id="menu-new" class="menu">
          <ul> ... </ul>
      </div>
   </div>
</div>

/* CSS for styling */

.btn.is-active { color: #000; }
.btn.is-active + .menu { display: block; }
```



I prefer this approach over applying a state class to a parent element as the state is more accurately combined with the module in which it applies. It still has the dependency of tying the menu HTML with the button HTML: one has to come immediately after the other. If you can establish that consistency in your project then this is an approach that can work well for you.

#### Why parent and sibling states are problematic

The reason why this approach can be more troublesome over just applying a state to each module is that it is no longer clear where this rule set should go. The menu is no longer just a menu. It's a button menu. If you needed to modify the active state for this module, do you find the CSS in with the button CSS or is it in with the menu CSS?

All that to say that applying a state to each button is the preferred approach. You're creating a better separation between the modules, making your site easier to test, develop, and scale.

### Handling State Change with Attribute Selectors

Depending on your browser support, you can also take advantage of attribute selectors to handle state change. This can be useful for:

* isolating states from layout and module classes
* allowing easier transitions between multiple states

Let's take a look at an example of a button that can be in multiple states such as default, pressed or disabled.

You may choose to use a sub-module naming convention.



Sub-module naming convention

```
.btn { color: #333; } 
.btn-pressed { color: #000; } 
.btn-disabled { opacity: .5; pointer-events: none; }
```



If a button needs to be toggled between states then it might make more sense to use a state naming convention.



State naming convention

```
.btn { color: #333; } 
.is-pressed { color: #000; } 
.is-disabled { opacity: .5; pointer-events: none; }
```



I like the comparison between these two examples because it highlights that SMACSS is often about clarity and naming convention. I would be happy to see either of these two examples within a project. Now let's take a look at another approach: *attribute selectors*.



Attribute selectors convention

```
.btn[data-state=default] { color: #333; } 
.btn[data-state=pressed] { color: #000; } 
.btn[data-state=disabled] { opacity: .5; pointer-events: none; }

<!-- HTML -->
<button class="btn" data-state="disabled">Disabled</button>
```



The `data-` prefix on the attribute is part of the HTML5 specification that allows you to make up attribute names and place them within the data namespace so as not to conflict with future HTML attribute specifications. Changing the state of a button doesn't require removing classes and adding classes. It just requires changing the value of a single attribute.



Changing State with jQuery

```
// bind a click handler to each button
$(".btn").bind("click", function(){
    // change the state to pressed
    $(this).attr('data-state', 'pressed');
});
```



Admittedly, with JavaScript libraries like jQuery, manipulating classes for state management isn't complicated. jQuery has methods like `hasClass`, `addClass`, and `toggleClass` that make working with class names really easy.

Suffice it to say, you have plenty of choices in the way you can represent state.

### Class-based State Change with CSS Animations

Animations are an interesting beast and some may argue that it is defining behaviour in a layer where it shouldn’t be defined. CSS is for styling, after all. JavaScript is for behaviour.

The distinction here is to understand that CSS defines a visual *state*. We can use JavaScript to switch the state of an element on our page. JavaScript should not be used to describe the state, though. That is, it shouldn’t be used to add inline styles.

Historically, we have used JavaScript to create animation because it was the only way we had available to do so ([HTML+TIME](http://www.w3.org/TR/NOTE-HTMLplusTIME)notwithstanding).

When we think of things in these terms, it can help shape how we approach various situations. For example, it wouldn’t be unusual to have a message appear on the page for a short period of time and then fade out.



JavaScript handling state change

```
function showMessage (s) {
    var el = document.getElementById('message');
    el.innerHTML = s;

    /* set state */
    el.className = 'is-visible'; 
    setTimeout(function(){
        /* set state back */
        el.className = 'is-hidden';
    }, 3000);
}
```



The message state changes from hidden to visible and back to hidden again. The JavaScript handles the changes in these states and then CSS can be used to animate between these—using either CSS transitions or animations.



CSS handling the transition

```

@keyframes fade {
    0% { opacity:0; display:block; }
  100% { opacity:1; display:block; }
}

.is-visible {
    display: block;
    animation: fade 2s;
}

.is-hidden {
    display: none;
    animation: fade 2s reverse;
}

```



I admit, this last example wouldn’t actually work. Unfortunately, the current animation specification and browser implementations won’t allow for us to specify non-animatable properties in our animation. Thankfully, the spec is still changing and should have this added eventually—with browser implementations to follow. In the meantime, we need to do something like the following.



Animations in current browsers

```

@-webkit-keyframes fade {
    0% { opacity:0;  }
  100% { opacity:1; display:block; }
}

.is-visible {
    opacity: 1;
    animation: fade 2s;
}

.is-hidden {
    opacity: 0;
    animation: fade 2s reverse;
}

.is-removed {
    display: none;
}

/* and then our javascript */
function showMessage (s) {
    var el = document.getElementById('message');
    el.innerHTML = s;

    /* set state */
    el.className = 'is-visible'; 
    setTimeout(function(){
        /* set state back */
        el.className = 'is-hidden';
        setTimeout(function(){
            el.className = 'is-removed';
        }, 2000);
    }, 3000);
}

```



In this case, I’ve changed it to still do the animation but then to use JavaScript to remove the element from flow after the animation should be done.

In this way, we maintain the separation between style (aka state) and behaviour.

## Change via Pseudo-class

As we've just seen, we can use classes and attributes to handle defining state changes on a module. However, CSS offers up plenty of pseudo-classes that can also help us manage states and state change.

From CSS2.1, the three most useful pseudo-classes are the "dynamic" ones that react to user interaction: `:hover`, `:focus`, and `:active`. CSS3 adds a number of new pseudo-classes, most of which style based on HTML structure (such as `:nth-child` or `:last-child`). There are a number of UI pseudo-classes in CSS3 that can respond to form interactions, which can also be quite handy.

The default state for a module is normally defined without a pseudo-class. Define the pseudo-classes as a secondary state of the module.



Defining States with pseudo-classes

```

.btn {
    background-color: #333; /* gray */
}

.btn:hover {
    background-color: #336; /* blueish */
}

.btn:focus {
    /* blueish focus ring */
    box-shadow: 0 0 3px rgba(48,48,96,.3); 
}
```



As modules are sub-classed, it can potentially get complicated as you may need to design pseudo-class states for the sub-modules, as well.



Defining sub-module States with pseudo-classes

```

.btn {
    background-color: #333; /* gray */
}

.btn:hover {
    background-color: #336; /* blueish */
}

.btn:focus {
    /* blueish focus ring */
    box-shadow: 0 0 3px rgba(48,48,96,.3); 
}

/* a default button state is the default choice from a
 * selection of buttons 
 */
.btn-default {
    background-color: #DEDB12; /* yellowish */
}

.btn-default:hover {
    background-color: #B8B50B; /* darker yellow */
}

/* no need to define a different focus state */
```



In this last code example, we have essentially created 5 variations of a single module: a primary module, a sub-module, and then the pseudo-class states that they could appear in. It can get even more complicated when we introduce class-based states on top of each of these.



Modules, sub-modules, class states and pseudo-class states. Oh my.

```

.btn { ... }
.btn:hover { ... }
.btn:focus { ... }

.btn-default { ... }
.btn-default:hover { ... }

.btn.is-pressed { ... }
.btn.is-pressed:hover { ... }

.btn-default.is-pressed { ... }
.btn-default.is-pressed:hover { ... }
```



Thankfully, few modules in your interface are going to need quite this array of state management. However, it is clear that proper organization of your styles will ensure your project is easier to maintain.

## Change via Media Query

While state changes via classes and pseudo-classes are fairly commonplace, media queries are fast becoming another approach to managing state change—a way that has traditionally only been possible with JavaScript. Adaptive design and [Responsive Web Design](http://www.alistapart.com/articles/responsive-web-design/)use media queries to react to various criteria. Print style sheets were one of the first media queries that allowed us to define how elements should look when printed on a page.

A media query can be defined as a separate style sheet using the media attribute on the link element or it can be defined within a `@media` block within a specific style sheet.



Linking stylesheets

```
<link href="main.css" rel="stylesheet">
<link href="print.css" rel="stylesheet" media="print">

/* inside main.css */
@media screen and (max-width: 400px) {
    #content { float: none; }
}
```



Most examples of media queries define a break point and then throw all styles that pertain to that particular break point and place them inside.

With SMACSS, the intent is to keep the styles that pertain to a specific module with the rest of the module. That means that instead of having a single break point, either in a main CSS file or in a separate media query style sheet, place media queries around the module states.



Modular Media Queries

```

/* default state for nav items */
.nav > li {
   float: left;
}

/* alternate state for nav items on small screens */
@media screen and (max-width: 400px) {
    .nav > li { float: none; }
}

... elsewhere for layout ...

/* default layout */ 
.content { 
    float: left;
    width: 75%;
}

.sidebar {
    float: right;
    width: 25%;
}

/* alternate state for layout on small screens */
@media screen and (max-width: 400px) {
    .content, .sidebar { 
        float: none;
        width: auto; 
    }
}
```



Yes, this does mean that the media query declaration may (and likely will) get declared multiple times but it also allows for all information about a module to be kept together. Remember, keeping the module information together (especially in its own CSS file) allows for isolated testing of the module and (depending on how you build your application) allows assets such as modularized templates and CSS to be loaded after the initial page has been loaded.

## It's all about State

This chapter reviewed the three types of state change: class, pseudo-class, and media query. Thinking about your interface not only modularly but as a representation of those modules in various states will make it easier to separate styles appropriately and build sites that are easier to maintain.

