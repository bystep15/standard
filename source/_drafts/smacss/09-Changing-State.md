# 状态改变（Changing State）

[原文](https://smacss.com/book/state)

You’ve got a Photoshop document open in front of you and you have been told to turn it into the magic that is HTML and CSS (with maybe a little JavaScript thrown in for good measure).

在讨论以下内容之前我默认在您面前已经打开了的Photoshop的文档，并且您已经掌握如何将它转换为HTML和CSS（可能使用JavaScript是一个不错的方法）。

It may seem straightforward to start mapping things directly from the composition to the code. However, various components on your page are likely to need to be represented in various states. There is the default state that something should appear in and then what it should look like when the state changes.

从图片的构成到代码的实现看起来似乎很简单。 但是，页面上的不同组件可能需要代表不同的状态。在此基础上应该有一个默认的状态，并且当状态改变时，应当明确它们的样式看起来会有什么样的变化。

## 什么是状态改变（What is a state change?）

State changes are represented in one of three ways:

1. class name
2. pseudo-class
3. media query

状态改变代表着以下三种方式中的一种：

1. 类名
2. 伪类
3. 媒体查询

A class name change happens with JavaScript. Via some interaction, be it moving the mouse around, hitting something on the keyboard, or some other event occurring. An element gets a new class applied and then the visual appearance changes.

类名的改变是通过JavaScript实现的。这些改变无论是移动鼠标，敲击键盘上的某个按键，还是发生其他事件，都是通过一些交互实现的。一个元素获取到一个新类，从而导致视觉外观的改变。

A pseudo-class change is done via any number of pseudo-classes, and there are a lot. In these cases, we no longer have to rely on JavaScript to describe the state change. Pseudo-classes are still limited in that we can only style changes to elements that are descendants or siblings of the element in which the pseudo-class applies. Otherwise, we are back to using JavaScript.

伪类的改变是通过任意数量的伪类实现的，并且这些伪类还很多。在这些情况下，我们不再需要依靠JavaScript来表述状态的改变。伪类仍然是有一些局限性的，因为我们只能对元素进行样式上的变化，并且这些元素是伪类元素的后代或兄弟元素。否则的话，我们只能使用JavaScript。

Lastly, media queries describe how things should be styled under defined criteria, such as different viewport sizes.

最后，媒体查询描述了如何按照规定的标准（例如，不同的窗口大小）来设置样式

With a module-based system, it is important to consider state-based design as applied to each of the modules. When you actively ask yourself, “what is the default state,” then you’ll find yourself thinking proactively about progressive enhancement. It also can have you approaching issues slightly differently.

对于一个基于模块的系统而言，考虑到应用于每个模块中基于状态的设计是很重要的。当您问自己“什么是默认状态”时，您会发现自己主动思考的能力会提高。它也可以让你对于不同的问题有不同的处理方法。

## 通过类名改变（Change via Class Name）

For the most part, class name changes are straightforward. These are applied to elements that take on a different state. For example, a user clicks on a disclosure icon to show and hide an element on the page.

大多数情况下，类名更改很简单。类名的改变适用于呈现元素的不同状态。例如，用户点击显示图标以显示和隐藏页面上的元素。

通过JavaScript改变类名来改变状态（JavaScript changing state via class name）

```
// with jQuery
$('.btn-close').click(function(){ 
    $(this).parents('.dialog').addClass('is-hidden');        
})
```

The jQuery example adds a click event handler to every element with the `btn-close` class name. When the user clicks on the button, it takes the event source and works up the DOM tree to find the ancestor element with the class of `dialog` on it. Then it applies the `is-hidden` state class.

上述jQuery的例子向每个具有`btn-close`类名的元素添加了一个点击事件。 当用户点击按钮时，它将获取事件源并在DOM树上查找具有`dialog`类的祖先元素。 然后对它应用`is-hidden`状态类。

Other times, a state change has a greater impact.

其他情况下，一个状态的改变会有更大的影响。

A common interface design pattern is that of a button being pressed and displaying a menu. In this case, the menu changes to a pressed state and the menu changes to a visible state. What options do we have for handling this change? It depends heavily on your HTML structure. For example, at Yahoo!, menus get loaded at request time and are, therefore, inserted at the top of the DOM. We had used a naming convention to hook the two together.

一个常见的界面设计模式是按下按钮并显示菜单。在这种情况下，菜单按钮变为按下状态，并且菜单内容变为可见状态。我们有什么选项来处理这种变化么？请注意，这很大程度上取决于您HTML的结构。 例如，在雅虎的站点中，菜单在请求时被加载，因此，它被插入在DOM的顶部。下面，我们会使用了一个命名约束将两者联系在一起。

按钮和菜单在一个文件中的不同部分（Button and menu in separate parts of the same document）

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

将数据绑定到一个JavaScript的点击事件上，然后说，“嘿，你想要加载一个菜单”。然后会根据按钮的ID找到与之匹配的菜单。下面的代码是在jQuery这种情况是如何实现的：

用jQuery加载菜单（Loading Menu with jQuery）

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

如代码所示，单个项目的状态改变通过JavaScript在两个不同的部件中的两个不同地方上进行修改的。

But what if the menu actually resided right next to the button?

但是，如果菜单是放在按钮的旁边呢？

按钮和菜单位于文档中的同一位置（Button and menu in the same part of the document）

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

前面的代码将完全相同，可以保持不变。但是，我们也有其他的选择。你的第一反应可能是对父元素添加一个类，并从那里设置按钮和菜单的样式。

向父元素添加一个类来设置子元素的样式（Adding a class to parent element to style child elements）

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

这种方法的问题是HTML结构现都被捆绑起来了。因此我们在这里必须添加一个容器元素，菜单和按钮必须存在于容器元素中。对此我们只能希望在这个工具栏里没有其他的按钮了！

Another approach to this is to apply the active class to the button as we did before and use the sibling selector to activate the menu.

另一种方法是现将active类添加到按钮上，然后用兄弟选择器来激活菜单。

使用兄弟选择器激活菜单（Activating the menu with a sibling selector）

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

我更喜欢将状态类应用到父元素的方法，因为状态可以更准确地与其应用的模块相结合使用。它仍会将菜单HTML与HTML按钮绑定起来：两者必须相互结合。如果您可以在您的项目中建立起一致性，那么这会是一个对您工作有利的事情。

#### 为什么父类和子类的状态是有问题的（Why parent and sibling states are problematic）

The reason why this approach can be more troublesome over just applying a state to each module is that it is no longer clear where this rule set should go. The menu is no longer just a menu. It's a button menu. If you needed to modify the active state for this module, do you find the CSS in with the button CSS or is it in with the menu CSS?

这种方法之所以会比将状态应用到每个模块更麻烦，是因为将这个规则集放置在哪里是不明确的。如果这样做的话，单不再只是一个菜单。而是一个菜单按钮。如果您需要修改这个模块的激活状态，您应该从按钮CSS中来查找CSS，还是从菜单CSS中查找呢？

All that to say that applying a state to each button is the preferred approach. You're creating a better separation between the modules, making your site easier to test, develop, and scale.

基于以上所说的一切，为每个按钮的应用状态是一个首选的方法。您应当在模块之间有更好的分离，从而使您的网站更易于测试，开发和扩展。

### 用属性选择器来处理状态的改变（Handling State Change with Attribute Selectors）

Depending on your browser support, you can also take advantage of attribute selectors to handle state change. This can be useful for:

* isolating states from layout and module classes
* allowing easier transitions between multiple states

根据您的浏览器的支持情况，您还可以利用属性选择器来处理状态更改。 这可以用于：

* 从布局和模板类中分离状态
* 在多个状态之间可以更容易的转换

Let's take a look at an example of a button that can be in multiple states such as default, pressed or disabled.

我们来看一个按钮的例子，它可以处于如默认，按下或禁用等多个状态。

You may choose to use a sub-module naming convention.

您可以选择使用子模块来命名约束。

子模块命名约束（Sub-module naming convention）

```
.btn { color: #333; } 
.btn-pressed { color: #000; } 
.btn-disabled { opacity: .5; pointer-events: none; }
```

If a button needs to be toggled between states then it might make more sense to use a state naming convention.

如果一个按钮需要在状态之间切换，那么使用状态命名约束可能更有意义。

状态命名约束（State naming convention）

```
.btn { color: #333; } 
.is-pressed { color: #000; } 
.is-disabled { opacity: .5; pointer-events: none; }
```

I like the comparison between these two examples because it highlights that SMACSS is often about clarity and naming convention. I would be happy to see either of these two examples within a project. Now let's take a look at another approach: attribute selectors.

我喜欢这两个例子之间的对比，因为它强调了SMACSS往往是对于内容和命名约束往往是清晰明了的。我很高兴看到这个项目中的这两个例子。现在让我们看看另一种方法：属性选择器。

属性选择器约束（Attribute selectors convention）

```
.btn[data-state=default] { color: #333; } 
.btn[data-state=pressed] { color: #000; } 
.btn[data-state=disabled] { opacity: .5; pointer-events: none; }

<!-- HTML -->
<button class="btn" data-state="disabled">Disabled</button>
```

The `data-` prefix on the attribute is part of the HTML5 specification that allows you to make up attribute names and place them within the data namespace so as not to conflict with future HTML attribute specifications. Changing the state of a button doesn't require removing classes and adding classes. It just requires changing the value of a single attribute.

属性上的`data-`前缀是HTML5规范的一部分，它允许您为属性创建名称并将其放置在数据命名空间中，以免与将来的HTML属性规范产生冲突。更改按钮的状态不需要删除类和添加类。它只需要改变一个属性的值即可。

使用jQuery改变状态（Changing State with jQuery）

```
// bind a click handler to each button
$(".btn").bind("click", function(){
    // change the state to pressed
    $(this).attr('data-state', 'pressed');
});
```

Admittedly, with JavaScript libraries like jQuery, manipulating classes for state management isn't complicated. jQuery has methods like `hasClass`, `addClass`, and `toggleClass` that make working with class names really easy.

诚然，在像jQuery这样的JavaScript库中，操纵负载状态管理的类并不复杂。jQuery有像`hasClass`，`addClass`和`toggleClass`这样的方法，使得类的命名工作变得非常简单。

Suffice it to say, you have plenty of choices in the way you can represent state.

只要您说明一下，您就可以有很多个选择来表达您需要的状态。

### 使用CSS动画实现基于类的状态的改变（Class-based State Change with CSS Animations）

Animations are an interesting beast and some may argue that it is defining behaviour in a layer where it shouldn’t be defined. CSS is for styling, after all. JavaScript is for behaviour.

动画是一个有趣的东西，有些人可能会争辩说，它不应该在定义行为的层中定义。毕竟，CSS是创建样式的。而JavaScript是为了行为表现的。

The distinction here is to understand that CSS defines a visual state. We can use JavaScript to switch the state of an element on our page. JavaScript should not be used to describe the state, though. That is, it shouldn’t be used to add inline styles.

这里的区别是CSS定义了一个可视化的状态。我们可以使用JavaScript来切换页面上元素的状态。但是JavaScript不应该被用来描述状态。也就是说，JavaScript不应该用来添加内联样式。

Historically, we have used JavaScript to create animation because it was the only way we had available to do so ([HTML+TIME](http://www.w3.org/TR/NOTE-HTMLplusTIME)notwithstanding).

从以往的情况来看，我们使用JavaScript来创建动画，是因为这是我们唯一可用的方法了（虽然[HTML + TIME](http://www.w3.org/TR/NOTE-HTMLplusTIME)也可以）。

When we think of things in these terms, it can help shape how we approach various situations. For example, it wouldn’t be unusual to have a message appear on the page for a short period of time and then fade out.

当我们用这些术语来思考事物时，它可以帮助我们如何处理各种情况。例如，在页面上短时间显示一条消息然后淡出并不罕见。

使用JavaScript来改变状态（JavaScript handling state change）

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

消息状态从隐藏变为可见并且再次变回隐藏。这里是通过JavaScript来处理这些状态的变化，然后使用CSS在这些状态之间进行处理（使用CSS转换或动画）。

CSS处理转换（CSS handling the transition）

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

我承认，这最后一个例子实际上不会运行。不幸的是，当前的动画规范和浏览器支持情况并不允许我们在动画中指定非动画的属性。不过值得庆幸的是，这个规范目前还在改动之中，随着浏览器的支持，最终还是会有这个属性的添加。同时，我们需要实现如下的事情。

现在浏览器中的动画（Animations in current browsers）

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

在这种情况下，我已经改变它，并让它继续执行动画，当动画执行完后，使用JavaScript从数据流中删除动画元素。


In this way, we maintain the separation between style (aka state) and behaviour.

这样，我们可以保持样式（又称为状态）和行为之间相分离。

## 通过伪类进行改变（Change via Pseudo-class）

As we've just seen, we can use classes and attributes to handle defining state changes on a module. However, CSS offers up plenty of pseudo-classes that can also help us manage states and state change.

正如我们刚刚看到的那样，我们可以使用类和属性来处理在模块上定义的状态变化。但是，CSS提供了大量的伪类，也可以帮助我们管理状态和它们之间的变化。

From CSS2.1, the three most useful pseudo-classes are the "dynamic" ones that react to user interaction: `:hover`, `:focus`, and `:active`. CSS3 adds a number of new pseudo-classes, most of which style based on HTML structure (such as `:nth-child` or `:last-child`). There are a number of UI pseudo-classes in CSS3 that can respond to form interactions, which can also be quite handy.

从CSS2.1开始，三个最有用的伪类是可以对用户交互作出反应的“动态”类`:hover`，`:focus`和`:active`。CSS3增加了一些新的伪类，其中大部分是基于HTML结构（例如：`nth-child`或`last-child`）的样式。在CSS3中有许多UI方面的伪类可以响应表单的交互，这也可以非常方便。

The default state for a module is normally defined without a pseudo-class. Define the pseudo-classes as a secondary state of the module.

一个模块的默认状态通常是没有伪类定义的。我们通常将伪类定义为模块的第二状态。

使用伪类定义状态（Defining States with pseudo-classes）

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

由于模块是分类的，因此可能会带来潜在的复杂性，因为您可能还需要为子模块设计伪类状态。

使用伪类定义子模块的状态（Defining sub-module States with pseudo-classes）

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

在最后一个代码示例中，我们基本上创建了5个不同形式的单一模块：一个是主模块，一个是子模块，和包含它们表现的伪类状态。甚至当我们引入基于类的状态时，它将会变得更加复杂。

Modules, sub-modules, class states and pseudo-class states. Oh my.

模块，子模块，类的状态和伪类状态。我的天。

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

值得庆幸的是，在您的界面中，很少有模块需要这么多的状态管理。但是，很明显，正确地管理您的样式将确保您的项目更容易维护。

## 通过媒体查询改变（Change via Media Query）

While state changes via classes and pseudo-classes are fairly commonplace, media queries are fast becoming another approach to managing state change—a way that has traditionally only been possible with JavaScript. Adaptive design and [Responsive Web Design](http://www.alistapart.com/articles/responsive-web-design/)use media queries to react to various criteria. Print style sheets were one of the first media queries that allowed us to define how elements should look when printed on a page.

虽然通过类和伪类进行状态更改更加普遍，但媒体查询正在迅速的成为管理状态更改的另一种方法，传统上这原本只能通过JavaScript才能实现。自适应设计和[响应式Web设计](http://www.alistapart.com/articles/responsive-web-design/)都使用媒体查询来满足各种标准。打印样式表是第一个允许我们定义元素在页面上打印时的外观的媒体查询之一。

A media query can be defined as a separate style sheet using the media attribute on the link element or it can be defined within a `@media` block within a specific style sheet.

媒体查询可以使用链接元素上的媒体属性定义为单独的样式表，或者可以使用`@media`块中定义特殊的样式表。

链接样式表（Linking stylesheets）

```
<link href="main.css" rel="stylesheet">
<link href="print.css" rel="stylesheet" media="print">

/* inside main.css */
@media screen and (max-width: 400px) {
    #content { float: none; }
}
```

Most examples of media queries define a break point and then throw all styles that pertain to that particular break point and place them inside.

大多数媒体查询的例子都是定义一个断点，然后选择与这个断点相关的所有样式，并将它们放置在CSS中。

With SMACSS, the intent is to keep the styles that pertain to a specific module with the rest of the module. That means that instead of having a single break point, either in a main CSS file or in a separate media query style sheet, place media queries around the module states.

对于SMACSS来说，媒体查询的意思是将特定模块相关的样式和模块的其余部分保持一致。这意味着，无论是在主CSS文件还是在单独的媒体查询样式表中，都会存在一个断点，而不是在模块状态周围选择媒体查询

模块媒体查询（Modular Media Queries）

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

的确，这确实意味着媒体查询可能（也很可能会）多次声明，但是它也允许关于模块的所有信息都保持在一起。请记住，将模块信息（特别是它自己的CSS文件中）保留在一起是允许对模块进行单独测试（这取决于您构建应用程序的方式）和在加载初始页面之后再加载模块化模板和CSS等资源的。

## 以上是关于状态的所有信息（It's all about State）

This chapter reviewed the three types of state change: class, pseudo-class, and media query. Thinking about your interface not only modularly but as a representation of those modules in various states will make it easier to separate styles appropriately and build sites that are easier to maintain.

这一章节回顾了三种类型的状态变化：类，伪类和媒体查询。您要做的不仅是以模块化的角度来考虑界面，还需要考虑这些模块在各种状态下的表示方式。通过这样做，可以使分离样式更容易，也可以构建更容易维护的站点。

