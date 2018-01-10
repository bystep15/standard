# 基本规范（Base Rules）

[原文](https://smacss.com/book/type-base)

A Base rule is applied to an element using an element selector, a descendent selector, or a child selector, along with any pseudo-classes. It doesn’t include any class or ID selectors. It is defining the default styling for how that element should look in all occurrences on the page.

一个基本的原则会应用在元素的元素选择器，后代选择器，子选择器或任何伪类。 但不包括任何类或ID选择器。 这个原则定义了该元素在所有页面上的默认样式。

基本样式的例子（Example Base Styles）

```
body, form {
    margin: 0;
    padding: 0;
}

a {
    color: #039;
}

a:hover {
    color: #03F;    
}

```
Base styles include setting heading sizes, default link styles, default font styles, and body backgrounds. There should be no need to use `!important` in a Base style.

基本的样式设置了包括标题的大小，默认的链接样式，默认的字体样式和背景图片。注意，在基本样式中不应该使用`!important`。

I highly recommended that you specify a body background. Some users may define their own background as something other than white. If you work off the expectation that the background will be white, your design may look broken. Worse, your font colour choice may clash with the user’s setting and make your site unusable.

我强烈建议您指定主体的背景。有些用户可能会将自己的背景定义为白色以外的其他背景色。 如果您的工作背景是白色的，那您的背景看起来会格格不入。 更糟糕的是，您选择的字体颜色可能与用户的设置的样式有冲突，并使您的网站无法正常展示。

## CSS重置（CSS Resets）

A CSS Reset is a set of Base styles designed to strip out—or reset—the default margin, padding, and other properties. Its purpose is to define a consistent foundation across browsers to build the site on.

CSS重置是一组基本的样式，用于去除或重置默认边距，填充和其他的属性。它目的是为了在不同的浏览器之间，确定网站的基本样式的一致性。

Many reset frameworks can be overly aggressive and can introduce more problems than they solve. Removing margin and padding from elements only to introduce them again creates duplicated effort and increases the amount of code needed to be sent to the client.

许多框架的重置可能有些做的过头了，并因此可能引入更多的问题。如果从元素中移除外边距和内边距仅仅是为了在之后的代码中重新引入这些属性，这只会增加复制量和需要发送到客户端的代码量。

Many find resetting styles a helpful tool in site development. Just be sure to understand the drawbacks of the framework you wish to use and plan accordingly.

许多人发现重置样式在网站站点中是一个很有开发工具。 只要确定要了解您希望使用的框架的缺陷并相应地进行规划即可。

Developing your own set of default styles that you consistently use from project to project can also be advantageous.

开发您自己的默认样式集合并在项目中持续的使用，这对于您的开发将会是很有利的。
