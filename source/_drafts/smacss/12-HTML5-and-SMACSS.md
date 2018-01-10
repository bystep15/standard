# HTML5和SMACSS（HTML5 and SMACSS）

[原文](https://smacss.com/book/html5)

As it turns out, it works just as well with HTML5 as it does with HTML4 or any other HTML you might be using with your CSS. That is because the SMACSS approach has two core goals:

1. Increase the semantic value of a section of HTML and content
2. Decrease the expectation of a specific HTML structure

事实证明，SMACSS在与HTML5一起使用时的表现与SMACSS和HTML4或其他您可以与CSS一起使用的HTML一起使用时表现一样良好。这是因为SMACSS有两个核心的目标：

1. 增加HTML和内容的语义性
2. 减少对特殊的HTML结构的期望

HTML5 introduces a number of new elements which can help us increase the semantic value of a section of HTML and content. Tags like `section`, `header`, and `aside` are more descriptive than a simple `div`. We have new input types that allow us to differentiate a numeric field from a date field from a text field. The extra tags and attributes have allowed us to be more descriptive. That is a good thing.

HTML5引入了一些新的元素，这些元素可以帮助我们提高一段HTML和内容的语义化。像`section`，`header`和`aside`这些标签就比简单的`div`的描述性更强。在HTML5中我们有了新的输入类型，这些输入类型可以让我们区分数字字段和文本字段中的日期字段。这些额外的标签和属性可以让我们的描述更具语义性。这是一件好事。

But even with our new tags to play with, the tags are not necessarily (or very likely) going to describe a very specific module on the page. Is a `nav` element always going to contain the exact same type and style of navigation?

但即便我们使用新的标签，这些新标签在页面中也不一定（或很可能）可以很好的描述特定的模块。比如，一个`nav`元素是否总是包含完全相同的导航类型和样式呢？

实践（implementation）

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

主导航在页面顶部使用水平导航，但是辅助导航（例如侧栏）则是垂直列出内容。类的名称说明了类型之间的区别。

Class names help describe our content in very specific ways—ways that are more specific than even HTML5 can provide. This serves our first goal of increasing the semantic value of a section of HTML.

类的名称用一种非常特殊的方式帮助我们描述内容，这种方式比HTML5提供的方法更特殊。这符合我们增加一段HTML语义化的第一个目的。

Your first instinct might be to do something like the following:

您的第一反应可能是这样的：

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

通过这样做，我们已经明白这些类只能用于`nav`元素。 如果我们的代码永远不会改变，这不会产生什么问题的。然而，本书的目的是描述可扩展的项目，所以让我们看一看这个项目中结构发生变化的例子。

Our primary navigation is only a single level but the client comes back and says we need to add drop down menus to every element. Our HTML structure changes.

我们的主导航只有一个级别，但是客户需要我们为每个元素添加一个下拉菜单。所以我们的HTML结构需要发生变化。

实践（implementation）

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

通过使用子导航，我们应该如何设置这些项目，使它们垂直排列而不是水平排列？

With the CSS that we already have, we would have to add a `<nav class="nav-secondary">` around each of the inner unordered lists to get the style that we want.

使用我们目前已有的CSS，我们必须在每个内部无序列表的周围添加`<nav class =“nav-secondary”>`来获得我们想要的样式。

We can augment the CSS to target the inner list items.

我们可以扩展CSS来定位内部列表项。

扩展CSS（Augmented  CSS）

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

另一种方法是不需要`nav`元素应用到我们的类，这有利于我们减少对特定HTML的期望的第二个目标。

SMACSS样式的CSS（SMACSS-style CSS）

```
.l-inline li { 
    display: inline-block;
}

.l-stacked li {
    display: block;
}

```

In this case, we have switched to indicate that these are Layout rules, since we are impacting how the individual modules (the list items) are to be contained. The `.l-stacked` class can be applied to the sub-navigation `ul`. This will create the result that we desire.

在这种情况下，我们已经转而指出了这些是布局规则，因为我们正在考虑如何结合各个模块（列表项）。`.l-stacked`类可以应用于子导航`ul`上。这会产生我们预期的结果。

Specifying the list item as a required child element still binds the Layout rules to specific HTML elements. There are certainly multiple ways to skin a cat, as the saying goes. For example, you might wish to say that all child elements will take on that style.

将列表项指定为必需的子元素仍然会将布局规则绑定到特定的HTML元素。我们有许多种可以实现目标的方式。例如，您可能想说所有的子元素都将采用这种风格。

SMACSS样式的CSS（SMACSS-style CSS）

```
.l-inline > * { 
    display: inline-block;
}

.l-stacked > * {
    display: block;
}

```

The downfall to this approach is that the rules will have to be evaluated for every single element on the page and not just the list items. The targeting of just direct descendants avoids too much traversal. This lets us use the inline and stacked classes on pretty much any element where we want the child elements to take on those styles.

这种方法的缺点是不仅仅是项目列表项，我们还必须对页面上的每一个元素进行评估。定位直接的后代可以避免很多遍历。这让我们可以在任何我们希望子元素采用这些样式的元素上使用内联类和堆栈类。

实践（implementation）

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

即使只是这个简单的例子，我们也要设法简化CSS，以此避免让选择器的使用更加复杂。同时也要保证对应的HTML代码也是可以理解的。

Remember the two goals: increase semantics and decrease reliance on specific HTML.

记住两点：增加语义化并减少特殊HTML的依赖性。

