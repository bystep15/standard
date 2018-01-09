# 主题规范（Theme Rules）

[原文](https://smacss.com/book/type-theme)

Theme Rules aren't as often used within a project and because of that, they aren't included as part of the core types. Some projects may have a need for them, though, as we did when working on Yahoo! Mail.

主题规则在实际项目中并不常用，因此，虽然有些像雅虎的邮箱系统中需要用到它们，但它们还是不被包含在核心类型中。

## 主题（Themes）

It is probably self-evident but a theme defines colours and images that give your application or site its look and feel. Separating the theme out into its own set of styles allows for those styles to be easily redefined for alternate themes.

主题可以定义颜色和图像，这对于是它的含义是不言而喻的，它为您的应用程序或网站提供了外观和样式。将主题自身的样式单独提取出来，可以让这个主题轻松地定义成其他的替代主题。

Themes can affect any of the primary types. It could override base styles like default link colours. It could change module elements such as chrome colours and borders. It could affect layout with different arrangements. It could also alter how states look.

主题可以影响任何主要的类型。它可以覆盖默认链接颜色等的基本样式。它可以改变像chorme的颜色和边框等的模块元素。它可能会对不同的布局有不同的影响。同时，也可以改变状态的样式。

Let’s say you have a dialog module that needs to have a border colour of blue, the border itself would be initially defined in the module and then the theme defines the colour:

假设您有一个对话框模块，需要有一个蓝色的边框颜色，边框本身可能最开始是在模块中定义的，然后在主题中重新定义颜色：

模块主题（Module Theming）

```
// in module-name.css
.mod {
    border: 1px solid;
}

// in theme.css
.mod {
    border-color: blue;
}
```

Themes could have class names that clearly indicate what styles are part of the theme and what aren’t. Just having a separate theme file should hopefully be enough.

主题是可以有类名的，您要清楚哪些样式会是主题的一部分，什么不是。并且只要有一个单独的主题文件就足够了。

At Yahoo! Mail, to help with maintaining consistency across all of our theme files—we have over 50—we use a Mustache template for our CSS that allows us to specify a number of colour values, a background image, and create a final CSS file for production.

在雅虎的邮箱系统中，为了帮助维持我们主题的文件一致性（这些文件超过了50个），我们使用Mustache模板为我们的CSS提供基本的样式，它允许我们指定一些颜色值，背景照片和最终用于生产环境的CSS文件。

## 字体规范（Typography）

Last but not least, there are font rules. Similar to themes, there are times when you need to redefine the fonts that are being used on a wholesale basis, such as with internationalization. Locales such as China and Korea have complex ideograms that are difficult to read at smaller font sizes. As a result, we create separate font files for each locale that redefine the font size for those components.

最近，字体规范引起了我们的注意。和主题类似，有时需要您重新批量定义字体类型，例如国际通用的字体。像中国和韩国地区的字体有复杂的表现含义，在较小的字体中比较难阅读。因此，我们为每个重新定义的字体大小类型的组件创建了单独的字体文件。


Font rules will normally affect base, module and state styles. Font styles won’t normally be specified at the layout level as layouts are intended for positioning and placement, not for stylistic changes like fonts and colours.

字体规范通常会影响基本规范，模块规范和状态样式。我们通常不会在布局的级别上指定字体的样式，因为布局是用于定位和放置内容的，而不是用于字体和颜色等的更改。

Like theme files, there may not be need to define actual font classes (like `f-large`). Your site should only have 3 to 6 different font-sizes. If you have more than 6 font sizes declared in your project, your users will not likely notice and you are making the site harder to maintain.

像主题文件一样，我们可能不需要定义实际的字体类型（如`f-large`）。您的网站通常应该只有3到6种不同大小的字体。 如果您的项目中声明的字体大小超过6个，那么您的用户可能并不会注意到这些，并且您站点可能会变得难以维护。
