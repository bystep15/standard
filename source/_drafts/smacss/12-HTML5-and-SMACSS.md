# HTML5 and SMACSS

[原文](https://smacss.com/book/html5)

As it turns out, it works just as well with HTML5 as it does with HTML4 or any other HTML you might be using with your CSS. That is because the SMACSS approach has two core goals:

1. Increase the semantic value of a section of HTML and content
2. Decrease the expectation of a specific HTML structure

HTML5 introduces a number of new elements which can help us increase the semantic value of a section of HTML and content. Tags like `section`, `header`, and `aside` are more descriptive than a simple `div`. We have new input types that allow us to differentiate a numeric field from a date field from a text field. The extra tags and attributes have allowed us to be more descriptive. That is a good thing.

But even with our new tags to play with, the tags are not necessarily (or very likely) going to describe a very specific module on the page. Is a `nav` element always going to contain the exact same type and style of navigation?



 implementation

```
<nav class="nav-primary">
    <h1>Primary Navigation</h1>
    <ul>…</ul>
</nav>

<nav class="nav-secondary">
    <h1>External Links</h1>
    <ul>…</ul>
</nav>

```



The primary navigation uses a horizontal navigation along the top of the page but the secondary navigation (for a sidebar, for example) lists items vertically. The class names provide differentiation between the types.

Class names help describe our content in very specific ways—ways that are more specific than even HTML5 can provide. This serves our first goal of increasing the semantic value of a section of HTML.

Your first instinct might be to do something like the following:



 CSS

```
nav.nav-primary li { 
    display: inline-block; 
}

nav.nav-secondary li {
    display: block;
}

```



In doing so, we have indicated that these classes may only be used on `nav` elements. If our code was never going to change, this would be okay. However, the intention of this book is to describe scalable projects, so let us look at an example of how things might change on this project.

Our primary navigation is only a single level but the client comes back and says we need to add drop down menus to every element. Our HTML structure changes.



 implementation

```
<nav class="nav-primary">
    <h1>Primary Navigation</h1>
    <ul>
        <li>About Us
            <ul>
                <li>Team</li>
                <li>Location</li>
            </ul>
        </li>
    </ul>
</nav>

```



With this sub-navigation, how do we style the items such that they are listed vertically and not horizontally?

With the CSS that we already have, we would have to add a `<nav class="nav-secondary">` around each of the inner unordered lists to get the style that we want.

We can augment the CSS to target the inner list items.



Augmented  CSS

```
nav.nav-primary li { 
    display: inline-block; 
}

nav.nav-secondary li,
nav.nav-primary li li {
    display: block;
}

```



Another alternative is to remove the need for a `nav` element to apply our class to, which works towards our secondary goal of decreasing the expectation of specific HTML.



SMACSS-style  CSS

```
.l-inline li { 
    display: inline-block;
}

.l-stacked li {
    display: block;
}

```



In this case, we have switched to indicate that these are Layout rules, since we are impacting how the individual modules (the list items) are to be contained. The `.l-stacked` class can be applied to the sub-navigation `ul`. This will create the result that we desire.

Specifying the list item as a required child element still binds the Layout rules to specific HTML elements. There are certainly multiple ways to skin a cat, as the saying goes. For example, you might wish to say that all child elements will take on that style.



SMACSS-style  CSS

```
.l-inline > * { 
    display: inline-block;
}

.l-stacked > * {
    display: block;
}

```



The downfall to this approach is that the rules will have to be evaluated for every single element on the page and not just the list items. The targeting of just direct descendants avoids too much traversal. This lets us use the inline and stacked classes on pretty much any element where we want the child elements to take on those styles.



 implementation

```
<nav class="l-inline">
    <h1>Primary Navigation</h1>
    <ul>
        <li>About Us
            <ul class="l-stacked">
                <li>Team</li>
                <li>Location</li>
            </ul>
        </li>
    </ul>
</nav>

```



Even with just this rather straightforward example, we managed to keep our CSS simple and avoided making our selectors more complex. The HTML is still understandable.

Remember the two goals: increase semantics and decrease reliance on specific HTML.

