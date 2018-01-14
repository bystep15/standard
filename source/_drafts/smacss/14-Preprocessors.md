# 预处理器（Preprocessors）

[原文](https://smacss.com/book/preprocessors)

As great as CSS is, it is still missing features that many designers and developers would like it to have. To help fill this void—and to help speed up development—tools have been created to make our lives easier.

像CSS一样，SMACSS仍缺少许多设计者和开发者希望拥有的特性。为了填补这个空白，并且加快开发速度，我们创建了一些工具来使这个流程更加轻松快捷。

One type of tool is the CSS preprocessor. I’ll review what a preprocessor is, what it can do, and how it can help you in building scalable and modular CSS.

其中一种方法是CSS预处理器。在这章内容中，我们将回顾一下什么是预处理器，它可以做什么，以及它是如何帮助您构建可扩展的模块化的CSS。

## 什么是预处理器？（What is a preprocessor?）

A CSS preprocessor allows you to use a special syntax in your CSS that is then compiled within your project. Some preprocessors try and stick as closely as possible to actual CSS syntax, whereas others try to simplify things as much as possible.

CSS预处理器允许您在您的项目中使用特殊的语法编辑您的CSS。其中一些预处理器试图尽可能贴近真实的CSS语法，而另一些则尝试尽可能地简化CSS。

Take a look at this example for the [Stylus](http://learnboost.github.com/stylus/) preprocessor.

让我们看一个[Stylus](http://learnboost.github.com/stylus/)预处理器的例子。

Stylus使用这种方式编码（Coding using Stylus）

```
@import 'vendor'

body
  font 12px Helvetica, Arial, sans-serif

a.button
  border-radius 5px
```

For those who know [Ruby](http://www.ruby-lang.org/en/) or [CoffeeScript](http://coffeescript.org/), this will feel familiar. It strips out the need for curly braces and semi-colons and relies on significant white space instead. The indentation indicates which properties apply to which rules. Property names never have spaces in them, which means that the first space after the property name must separate the property from the value.

对于那些知道[Ruby](http://www.ruby-lang.org/en/)或者[CoffeeScript](http://coffeescript.org/)的开发者来说，它们看起来是很相似的。它不再使用大括号和半大写字母，而是通过空白来表示。其中，缩进表示哪些属性适用于哪些规则。属性名称中没有空格，这意味着属性名称后必须添加一个空格来将属性与值分开。

In addition to Stylus, the two preprocessors that currently lead the market are [Sass](http://sass-lang.com/) (or similarly, [Compass](http://compass-style.org/)) and [Less](http://lesscss.org/).

除了Stylus之外，目前市场上其他流行的两款预处理器是[Sass](http://sass-lang.com/)（或类似的[Compass](http://compass-style.org/)）和[Less](http://lesscss.org/)。

### 安装预处理器（Installing a preprocessor）

One of the complaints, especially from designers not as familiar with the command line, is that these preprocessor tools can be complicated to install. Depending on your environment, they can be. Or, it can be as simple as dragging an application into your Applications folder.

它有一个缺点，就是这些预处理工具的安装可能非常复杂，特别是不熟悉命令行的设计者而言。这可能取决于您的开发环境，它可能非常复杂，也有可能像将应用程序拖到“应用程序”的文件夹中一样简单。

For installing Sass on a Mac, for example, I just hopped to the command line and typed:

现在我举个例子，对于在Mac上安装Sass而言，以下是对应的命令行内容：

安装Sass（Installing Sass）

```
sudo gem install sass
```

或者安装Compass（Or installing Compass）

```
sudo gem install compass
```

[Gem](http://rubygems.org/) is a command line tool from the Ruby world that acts as a package manager for installing applications and is pre-installed on recent versions of Mac OS X.

[Gem](http://rubygems.org/)是一个Ruby的命令行工具，它作为安装应用程序的包管理工具，预装在最新版本的Mac OS X上。

Once Sass is installed on my machine, I set Sass to watch a folder that I’m working on.

一旦Sass安装在我的机器上，我就可以设置Sass来查看我在处理的文件夹中的内容了。

运行Sass（Running Sass）

```
sass --watch before:after
```

Where before is the folder where all my .scss (precompiled CSS files) files are contained and `after` is where the post-compiled CSS files are placed. Any changes I make to my `.scss` files in the `before` folder are automatically compiled and placed as .css files in the `after` folder. This is handy for building and testing things quickly during development. (An .scss file is like a regular .css file but using the Sass syntax which I’ll explain later in this chapter.)

这里要注意两个文件夹，`before`是包含所有.scss（预编译的CSS文件）文件的文件夹，`after`文件夹是放置了编译过的CSS文件的文件夹。 我对`before`的文件夹中的`.scss`文件所做的任何更改都会自动编译为.css文件放在`after`文件夹中。这样可以在开发过程中快速构建和测试CSS代码。（.scss文件就像一个普通的.css文件一样，唯一的不同就是使用了本章后面将要解释的Sass语法。）

There is also the [Compass Mac app](http://compass.handlino.com/) that avoids the need of doing anything at the command line.

这里还有[基于Mac上的Compass应用程序](http://compass.handlino.com/)，它可以用来避免在命令行上执行任何操作。

Less uses npm, the [node package manager](https://github.com/isaacs/npm), which isn’t pre-installed. Therefore, you’d need to install both the node package manager and then Less after that. Less also has a JavaScript version that can run client-side during the development process.

Less使用npm[包管理器](https://github.com/isaacs/npm)，它不是预先安装的。 因此，您需要先安装包管理器，然后再安装Less。在开发过程中，Less也有一个可以运行客户端的JavaScript版本。

Less客户端的实现（Less’ Client-side Implementation）

```
<link rel="stylesheet/less" type="text/css" href="styles.less"><script src="less.js"></script>
```

Remember not to deploy this to a live site. Always compile the CSS before launch.

切记不要将`.less`文件部署到线上环境。始终保持在使用之前编译CSS。

Less命令行编译（Less Command Line Compilation）

```
lessc styles.less
```

Increasingly, site development is requiring command line tools. They can be a handy way to streamline your process and even get you out of a pickle that GUI tools sometimes can’t solve.

随着网站的开发，命令行工具也越来越重要。它们可以简化您的工作流程，甚至可以让您摆脱GUI工具有时无法解决的困境。

## 预处理器有用的特性（Useful features of a preprocessor）

Preprocessors offer up plenty of interesting features that can help make authoring CSS easier. A few of them are:

* Variables
* Operations
* Mixins
* Nesting
* Functions
* Interpolation
* File importing
* Extending

预处理器提供了许多有趣的功能，这些功能可以更容易地编写CSS。其中一些是：

* 变量
* 操作符
* 混合
* 嵌套
* 函数
* 插值
* 文件导入
* 扩展

What does all that mean? Let’s look deeper at some of them. (I’ll be using Sass for the examples moving forward but be aware that Less and Stylus also have similar approaches for the same concepts.)

这些都是什么呢？现在让我们更深入地研究其中的一些内容吧。（在此我将Sass作为示例，但请注意，Less和Stylus在同一概念上也有类似的方法。）

### 变量（Variables）

Anybody who has worked with CSS for more than an hour has likely wished for the ability to set a colour value once in a CSS file and then to re-use that colour anywhere else in the CSS. In Sass, you can define a variable prefacing a word with `$` and assigning it a value.

任何使用CSS超过一个小时的人都希望能够在CSS文件中设置一次颜色值，然后在其他任何地方复用这个颜色。在Sass中，您可以定义一个用`$`定义变量，并给它赋值。

使用变量（Using Variables）

```
$color: #369; 

body {
    color: $color;
}

.callout {
    border-color: $color;
}
```

The compiler will then convert this into the final file for deployment.

编译器会将它们转化为最终适合在开发环境的最终文件。

编译后的变量（Compiled Variables）

```
body {
    color: #369;
}

.callout {
    border-color: #369;
}
```

This is very handy for keeping site-wide changes all in one place. (Of note, the W3C is working on a draft specification of [CSS Variables](http://dev.w3.org/csswg/css-variables/).)

这种在一个地方来保持整个网站的属性值非常方便。（值得注意的是，W3C正在制定[CSS变量](http://dev.w3.org/csswg/css-variables/)的草案规范。）

### 嵌套（Nesting）

When coding CSS, it’s quite common to have a selector chain.

当编码CSS时，使用选择器链是很普遍的。

选择器链（Selector Chains）

```
.nav > li {
    float: left;
}

.nav > li > a {
    display: block;
}
```

Nesting allows these styles to be grouped more clearly in the precompiled CSS file.

嵌套运行这些样式可以预编译的CSS文件中有更清晰的分组。

Sass的嵌套（Nesting with Sass）

```
.nav {
    > li { 
        float: left;
        > a {
            display: block;
        }
    }
}
```

Each set of styles is nested inside the one above it. What does this look like generated?

每一个样式都嵌套在另一个样式里面，那最后生成的样式会使什么样的呢？

由Sass生成的CSS（Generated CSS from Sass）

```
.nav > li {
  float: left; }
  .nav > li > a {
    display: block; }
```

The nesting helps clarify which styles are grouped with what elements but not much different than just indenting the styles on your own. There is some saved typing from not having to type `.nav` every time.

嵌套可以更好地声明哪些样式与哪些元素是在同一个分组，最后的结果与您自己编写的样式没有多大区别。它会自动生成一些文本，让您不必每次都键入`.nav`。

### 混合（Mixins）

Mixins come with a lot of power. A mixin is a group of styles that can be re-used throughout your CSS. They can take parameters that customize the output of the mixin. One of the more common uses for mixins is to handle vendor prefixes. (Although they can really be used for any repetitive CSS rules.)

混合有很多的用处。mixin是一组可以在整个CSS文件中重用的样式集合。它们可以通过输入参数来自定义混合的输出。混合更常见的用途之一是处理供应商前缀。（虽然它们确实可以用于任何重复的CSS规则中。）

一个使用`border-radius`的混合的例子（An Example Mixin for `border-radius`）

```
@mixin border-radius($size) {
  -webkit-border-radius: $size;
     -moz-border-radius: $size;
          border-radius: $size;
}
```

Once you’ve declared a mixin, you can then call it from anywhere within your CSS using the `include` directive.

一旦您声明了一个混合，您可以通过使用`include``来直接在任何地方调用您的CSS。

一个使用`border-radius`的混合的例子（An Example Mixin for `border-radius`）

```
.callout {
    @include border-radius(5px);
}
```

The preprocessor will then compile that into this:

预处理器会将它们编辑成这样：

通过使用`border-radius`生成的CSS（Generated CSS for the `border-radius` mixin）

```
.callout {
  -webkit-border-radius: 5px;
     -moz-border-radius: 5px;
          border-radius: 5px;
}
```

### 函数（Functions）

The Mixins example already looks like a function. There is, however, the ability to do some powerful stuff with calculating values. For example, the `lighten` function takes a colour value and a percentage and will adjust the lightness of that value.

混合的示例看起来很像一个函数。然而，函数可以做一些更有价值，功能更强大的事情。例如，`lighten`函数可以输入一个颜色值和一个百分比，来调整该值的亮度。

通过函数来调整颜色值（Adjusting colour value using a function）

```
$btnColor: #036;
.btn { 
    background-color: $btnColor; 
}
.btn:hover { 
    background-color: lighten($btnColor, 20%); 
}
```

The preprocessor will then compile that into this:

预处理器会将它们编辑成这样：

使用函数编辑后的CSS（Compiled CSS with colour functions）

```
.btn { 
    background-color: #003366; 
}
.btn:hover { 
    background-color: #0066cc; 
}
```

Sass comes with a number of handy functions like this and Compass adds even more. (*If you’re going to use Sass, I highly recommend taking advantage of Compass, too.)*

Sass有许多类似的函数，Compass也增加了更多。（如果您要使用Sass，我认为您也可以使用Compass。）

### 扩展（Extensions）

Extensions are the ability to extend one module with the properties of another. In Sass, this is done with the `extend` directive.

扩展可以使用一个模块的属性扩展另一模块。在Sass中，这是通过`extend`指令完成的。

扩展Sass（Sass Extensions）

```
.btn { 
    display: block;
    padding: 5px 10px;
    background-color: #003366; 
}
.btn-default { 
    @extend .btn;
    background-color: #0066cc; 
}
```

The extension takes the styles from `btn` and applies them to `btn-default`. Sass is fairly smart, though. It doesn’t simply duplicate the rules in the second declaration. It creates a combination selector for the first set of rules.

扩展采用`btn`中的样式，并将其应用于`btn-default`。Sass很聪明，它不会简单地复制第二个声明中的规则，而是为第一组选择器的规则创建组合选择器。

使用Sass扩展特性编译后的CSS（Compiled CSS from Sass Extensions）

```
.btn, .btn-default {
  display: block;
  padding: 5px 10px;
  background-color: #003366; }

.btn-default {
  background-color: #0066cc; }
```

The extensions are limited to simple selectors. You couldn’t extend `#main .btn`, for example. We will come back to discuss extensions and how they impact the SMACSS approach later on in this chapter.

扩展名只适用于简单的选择器。例如，您无法扩展`#main .btn`。在后续的章节中，我们会继续讨论扩展，以及它们会如何影响SMACSS的方法。

### 更多（Even more）

This is only the tip of the iceberg when it comes to preprocessors. There are plenty of more features and examples on the respective web sites. It may seem daunting at first. Don’t feel the need to use every feature right away.

以上内容只是预处理器的冰山一角。在各自的网站上，有更多的功能和例子。但是它们适用的场合并不多。所以您不需要马上使用每个功能。

## 遇到麻烦，解决麻烦（Getting into and out of trouble）

You know the saying. “With great power comes great responsibility.” These preprocessors offer up lots of great functionality that can keep your precompiled CSS files nice and lean. However, once compiled, the magic can result in bloated CSS that is difficult to debug. In other words, you’re right back where you started. Bloated code is a possibility no matter how you code—whether by hand, by a WYSIWYG tool like Dreamweaver, or via a command line preprocessor. It’s also possible to create great code using any of these tools.

您也许听说过这样一句话“能力越大，责任越大”。这些预处理器提供了许多功能强大的特性，以此将保证编译后的CSS文件良构并简明直了。但是，一旦编译后，可能会出现CSS代码过于庞大，使得其难以调试。换句话说，您一下子就回到最初什么都没有的地步。无论你如何编码，是通过手工，还是通过Dreamweaver之类的所见即所得的工具，或者是通过命令行这样的预处理器，代码都有可能过庞大。当然，您也可以使用这些工具来编写出优秀的代码。

让我们来看一看它们是如何陷入麻烦的（Let’s look at where we can get into trouble.）

### 深度嵌套（Deep Nesting）

Once you start nesting, it can easily be taken too far. Imagine, if you will, something like this:

一旦您开始使用嵌套，您可以就会过度使用它。想象一下，如果您愿意，也许您会编写出这样的代码：

使用Sass进行深度嵌套（Deep Nesting with Sass）

```
#sidebar {
  width: 300px;
  .box {
    border-radius: 10px;
    background-color: #EEE;
    h2 {
      font-size: 14px;
      font-weight: bold;
    }
    ul {
      margin:0;
      padding:0;
      a {
        display:block;
      }
    }
  }
}
```

That wouldn’t be unusual to see. I’ve seen this quite a bit in working on existing Sass files. Here is what that generates into:

这样的代码并不罕见。我曾在现有的Sass文件上看到了这样的代码。以下是这些代码生成的内容：

使用Sass深度嵌套后编译的CSS（Compiled CSS using Deep Nesting with Sass）

```
#sidebar {
  width: 300px; }
  #sidebar .box {
    border-radius: 10px;
    background-color: #EEE; }
    #sidebar .box h2 {
      font-size: 14px;
      font-weight: bold; }
    #sidebar .box ul {
      margin: 0;
      padding: 0; }
      #sidebar .box ul a {
        display: block; }
```

#### 使用SMACSS进行嵌套（Nesting with SMACSS）

The SMACSS approach, by its very nature, minimizes deep nesting due to depth of applicability. The separation of layout and modules also avoids these issues. With SMACSS, the previous example would look more like this:

SMACSS方法就其本质而言，为了减少适用性的深度而让深度嵌套减到最小。布局和模块的分离也避免了这些问题。如果使用SMACSS，前面的例子看起来更像这样：

使用SMACSS进行深度嵌套（Deep Nesting with SMACSS）

```
#sidebar {
  width: 300px;
}

.box {
  border-radius: 10px;
  background-color: #EEE;
}

.box-header {
  font-size: 14px;
  font-weight: bold;
}

.box-body {
  margin: 0;
  padding: 0;
  a {
    display: block;
  }
}
```

There’s barely any nesting at all! That’s because we don’t need long selectors to get the styles that we want. It’s only when we need to target element selectors in a part of the module where we really need to worry about nesting.

这里几乎没有任何嵌套！那是因为我们不需要使用过长的选择器来获得我们想要的元素。只有在我们需要在模板中定位元素时我们才真正需要考虑嵌套。

Creating long selector chains just makes the browser work harder than it needs to when determining whether a style applies to the current element.

创建较长的选择器链只是让浏览器确定一个样式是否应用于当前元素上所需的工作更加复杂。

### 不必要的扩展（Unnecessary extending）

Returning back to our extension example of a default button extending from default button styles, let us look at that code example again.

回到我们默认按钮样式的扩展示例，让我们再看看代码示例。

使用Sass扩展一个按钮（Sass extension of a button）

```
.btn { 
    display: block;
    padding: 5px 10px;
    background-color: #003366; 
}
.btn-default { 
    @extend .btn;
    background-color: #0066cc; 
}
```

This allows us to do the following HTML, no longer needing to specify both the `btn` and `btn-default` classes on an element. Only one needs to be specified. We move the multiple declarations to the CSS from the HTML.

以上代码允许我们执行以下HTML，使得我们不再需要在元素上指定`btn`和`btn-default`类。这里只有一个需要指定。就是我们将多个声明从HTML上转移到了CSS上。

一个链接上类的应用（Application of the class on a link）

```
<a class="btn-default">My button</a>
```

Extending modules to create sub-modules are a way of avoiding having to define multiple classes in the HTML. The naming convention becomes more important in this situation. Having a module name of `btn` and a sub-module name of `small` would complicate things when the only class that gets applied is `small`. A small what? With `btn-small`, we can use the sub-module name on its own and still know what its purpose is for.

通过扩展模块来创建子模块是可以避免在HTML中定义多个类的一种方法。命名约定在这种情况下变得更为重要。当只有`small`应用时，使用名为`btn`的模块和`small`的子模块会使事情复杂化。一个小的什么？通过使用`btn-small`，我们可以使用子模块来命名，并且仍然知道它的目的是什么。

Looking at the SASS source, we can also see that the `btn-default` is a sub-module because of the use of `@extend`. Looking at the generated source, we can still see that `btn-default` is a sub-module because it will be grouped with the `btn` class.

看一下SASS源代码，我们也可以看到由于使用了@extend，`btn-default`是一个子模块。查看生成的源代码，我们仍然可以看到`btn-default`也是一个子模块，因为它与`btn`分在一起。

Where extending modules fails is when we extend across disparate modules.

当我们跨越不同模块时，我们会遇到模块扩展失败的情况。

Sass跨模块扩展（Sass extension across modules）

```
.box { 
    border-radius: 5px;
    box-shadow: 0 0 3px 0 #000000;
    background-color: #003366; 

}
.btn { 
    @extend .box;
    background-color: #0066cc; 
}
```

Extending across modules now ties these two concerns together. There is no longer one source of truth for where the styles for a module live.

现在，跨模块的扩展将这两部分结合在一起。这样模块的样式就不再只有一个来源了。

By tightly grouping everything in the CSS, you lose the ability to do just-in-time loading or to do conditional compilations depending on the components you need to load into your app. Button and box styles need to be loaded at the same time.

通过将所有内容紧密地结合在CSS中，您会失去即时加载或执行条件编译的能力，具体的情况取决于您需要加载到应用程序中的组件。注意，按钮和box的样式需要同时加载。

Extending even within the same module can introduce complexity to a project that does just-in-time loading of styles. For example, at Yahoo!, we would load the default button styles upon page load but only load secondary styles—such as those for compose—when that screen was requested. This kept the initial page load times very quick.

在同一个模块内使用扩展也会给一个需要及时加载样式的项目带来更多的麻烦。例如，在雅虎团队中，在获得请求时，我们在加载页面时需要加载默认的按钮样式，但是只加载次要的样式（如用于编写内容时的样式）。会使初始页面加载的非常快。

#### SMACSS扩展（SMACSS Extensions）

Using the SMACSS approach, extensions are just handled at the HTML level instead of the CSS level by defining the multiple classes in the HTML.

在使用SMACSS时，我们只要通过在HTML上定义多个类就可以在HTML级别上扩展，而不必在CSS级别上处理扩展。

在按钮上应用SMACSS模块类（Applying SMACSS module classes on a button）

```
<a class="btn btn-default">My button</a>
```

This has the added benefit of recognizing where the root element of a module is. When looking at compiled HTML in the browser, it may be difficult to discern where one module starts and where another one ends. Since root module names don't have any hyphenation, they stand out in the crowd.

它有一个额外的好处就是可以识别模块的根元素在哪里。在浏览器中查看编译的HTML时，可能很难区分一个模块是在哪里开始使用的，又是在哪里结束的。由于根模块的名称没有任何连字符，所以它特别好分辨。

I recognize that it begins to feel like classitis where multiple (seemingly unnecessary) classes are being added to the HTML. However, these classes aren't unnecessary. They clarify intent and increase the semantics of the element in question.

我认为它想于在HTML中添加多个（看似不必要的）类。但是，这些类并不是不必要的。他们声明了目的，并增加有关元素的语义。

### 过度使用混合（Overused Mixins）

Mixins are a handy way of avoiding repetition. However, CSS classes are also a handy way of avoiding reptition. If you have the same CSS being applied in multiple places, it may be worthwhile to move that style into its own class.

混合是一种避免的重复的便捷的方法。但是，CSS类也是避免重复的方便的选择。如果您在多个地方使用相同的CSS，那么把这部分样式转换成类可能是值得的。

Let’s say that all a collection of modules all share a similar visual style of a gray background and a blue rounded border. You might decide to create a mixin for this.

假设所有的模块的集合都共享一个灰色背景和蓝色圆形边框的视觉样式。name您可能会为此创建一个Mixins。

Sass为公共样式创建Mixin（Sass Mixin for common pattern）

```
@mixin theme-border {
  border: 2px solid #039;
  border-radius: 10px;
  background-color: #EEE;
} 

.callout {
  @include theme-border;
}

.summary {
  @include theme-border;
}
```

That gets compiled into this:

它会编译成这样：

使用Mixin编译后的CSS（Compiled CSS from Mixin）

```
.callout {
  border: 2px solid #039;
  border-radius: 10px;
  background-color: #EEE; }

.summary {
  border: 2px solid #039;
  border-radius: 10px;
  background-color: #EEE; }
```

#### SMACSS重用模式（SMACSS for Repetitive Patterns）

In this case, because it is a visual treatment being added to various containers, it’s worthwhile to place this into its own class.

在这种情况下，因为它是一个被添加到各种容器的视觉处理效果，因此将它放入自己的类是值得的。

为公共样式定义一个类（Defining a class for common pattern）

```
.theme-border {
  border: 2px solid #039;
  border-radius: 10px;
  background-color: #EEE;
} 

.callout {
}

.summary {
}
```

Then apply it to elements as required:

然后将它应用到需要它的元素上

应用这个类（Applying the class）

```
<div class="callout theme-border"></div>
<div class="summary theme-border"></div>
```

#### 参数化的混合（Parameterized Mixins）

To be clear, parameterized mixins offer up a lot of power that is just not possible with CSS and there is no equivalent approach to solve this beyond creating a lot of variations. The border-radius mixin example from early in this chapter is a great example of a parameterized mixin.

要清楚的是，带参数的mixin为我们提供了很多不只适用于CSS的功能，而且除了定义许多变量外，没有其他的方法可以解决这个问题。在本章前面的例子中，border-radius的混合就是参数化Mixin的一个很好的例子。

## 预处理器（Smack that preprocessor）

We’ve looked at a few common pitfalls of preprocessors in comparison to how we might accomplish it with SMACSS. The typical answer is: everything in moderation. Review the generated files and see if the final result is what you expect. If there is plenty of repetition then take a look at refactoring your approach.

与SMACSS相对比，我们已经看到了预处理器的一些常见缺陷。最典型的答案就是：一切都是合理的。回顾生成的文件，并查看最终的结果是否是您所期望的。如果有很多的重复的部分，那么重新看看您的方法是否得当。

Let’s look at a couple more ways in which a preprocessor can encourage better modularization of your code.

让我们来看看如何使用预处理器更好地处理模块化代码的方法。

### 使用嵌套来处理基于状态的媒体查询（State-based Media Queries with Nesting）

As we saw in the chapter, Changing State, media queries are one of the ways in which we can detect and manage state changes. Most tutorials demonstrate with a separate style sheet and stuff all of the styles related to that state into a single file. This separates a module definition into possibly multiple files, making it more difficult to manage.

正如我们在“状态改变”一章中所看到的，媒体查询是我们检测和管理状态变化的方法之一。大多数教程都使用单独的样式表来进行演示，并将与该状态相关的所有样式写入单个文件中。这样做将模块的定义分为了多个文件，使其更难以管理。

Sass allows media queries to be nested, allowing those state changes to be reflected where they belong: with the module.

Sass运行使用基于嵌套的媒体查询，并允许将这些状态反映到它们所处的模块当中。

Here is an example demonstrating nested media queries:

下面是一个基于嵌套的媒体查询的例子：

在Sass中嵌套媒体查询（Nested Media Queries in Sass）

```
.nav > li {
  width: 100%;

  @media screen and (min-width: 320px) {
      width: 100px;
      float: left;

  }

 @media screen and (min-width: 1200px) {
          width: 250px;
      }

}
```

The default state is defined and then the alternate states of that module are defined right from within that module. You can even embed media queries inside other media queries and Sass will concatenate the media query conditions.

在此，我们定义了默认状态，然后该在该模块中定义了模块可以改变的状态。您甚至可以将媒体查询嵌入到其他媒体查询中，Sass会自动处理嵌套的媒体查询。

Here is what the nested example generates into:

以下是嵌套生成的例子：

由Sass生成基于嵌套媒体查询的编译后的CSS（Compiled CSS from Nested Media Queries in Sass）

```
.nav > li {
   width: 100%; }
@media screen and (min-width: 320px) {
  .nav > li {
    width: 100px;
    float: left; } }
  @media screen and (min-width: 1200px) {
    .nav > li {
      width: 250px; } }
```

Sass creates the separate media queries and embeds the selector inside them. With this particular example, I specifically chose the default state to be the small screen view that would match for any screen under 320px. Then I switched to a floated navigation once it reaches a specific width. Finally, it changes the width at 1200px but does not re-declare the float. I like this inheritence that occurs from the default state through the various media queries.

Sass创建单独的媒体查询并在其中嵌入选择器。在这个特殊的例子中，我特别选择了默认状态为320px以下屏幕的小屏幕视图。然后，我切换到一个浮动的导航,一旦它达到特定的宽度。它就会将宽度定为1200像素并取消明浮动。我喜欢从默认状态通过各种媒体查询继承的方法。

Best of all, any alternate states for your module are declared with the module.

最重要的是，模块的任何可变状态都是在模块中声明的。

### 组织您的文件（Organizing Your Files）

Preprocessors encourage the separation of concerns that SMACSS recommends.

预处理器鼓励SMACSS推荐的分离要点的方法。

Here are some guidelines on how to separate the files in your project:

* Place all Base rules into their own file.
* Depending on the type of layouts you have, either place all of them into a single file or major layouts into separate files.
* Put each module into its own file.
* Depending on size of project, place sub-modules into their own file.
* Place global states into their own file.
* Place layout and module states, including media queries that affect those layouts and modules, into the module files.

以下是一些关于如何在您的项目中分离文件的要点：

* 将所有的基本规则置于它们本身的文件中。
* 根据您的布局类型，将其全部放入单个文件或将主要布局代码放入单独的文件中。
* 把每个模块放到它自己的文件中。
* 根据项目的大小，将子模块放入自己的文件中。
* 将全局状态放入自己的文件中。
* 将布局和模块状态（包括影响这些布局和模块的媒体查询）放置到模块文件中。

With files separated in this way, it’ll make your project easier to prototype. HTML templates can be created for individual components and the CSS and template for an individual component (or even a subset of components) can be tested in isolation of each other.

通过这种方式分隔文件，这将使您的项目更容易开发。这样我们可以为单独的组件创建HTML模板，并且可以测试单个组件（甚至是组件的子集）的CSS和模板。

Preprocessor-specific components such as mixins and variables should also be specified in their own files.

特定的预处理器的组件（如混合和变量）也应在其自己的文件中指定。

一个例子的目录结构（A sample directory structure）

```
 +-layout/
 | +-grid.scss
 | +-alternate.scss
 +-module/
 | +-callout.scss
 | +-bookmarks.scss
 | +-btn.scss
 | +-btn-compose.scss
 +-base.scss
 +-states.scss
 +-site-settings.scss
 +-mixins.scss
```

Finally, create the primary CSS file that will include the other files. For many sites, this might mean just including all of the files into the master style sheet. For projects with conditional asset loading, you can have container files that import only the necessary files for specific screens.

最后，创建包含其他文件的主要的CSS文件。对于许多网站来说，这可能意味着将所有的文件加到主样式表中。对于有条件加载的项目，您可以只输入基于特定屏幕所需的文件。

主文件中的内容（Inside the master file）

```
@import 
   "site-settings", 
   "mixins",
   "base",
   "states",
   "layout/grid",
   "module/btn",
   "module/bookmarks",
   "module/callout";
```

The precompiler will compile this into a single file for development or deployment.

预编译器会将其编译成单个文件进行开发或部署。


When you’re ready to launch, create a compressed version of your CSS file for deployment. (Your environment may have build scripts for deploying the rest of the application. Be sure to integrate preprocessor compilation in that final build process.)

当您准备发布时，它会创建一个用于部署CSS文件的压缩版本。（您的环境可能已经构建了用于部署应用程序其余部分的脚本，请务必在最终的构建过程中集成预处理器并进行编译。）

通过命令行使用Sass操作压缩的CSS文件（Command line for compressed CSS file using Sass）

```
sass -t compressed master.scss master.css
```

## 预处理器的总结（Post mortem on preprocessors）

We looked at what a preprocessor is and how to install one. We looked at some popular features and a few of the pitfalls. Finally, we looked at how preprocessors can make organizing your project easier. Preprocessors can definitely be a beneficial part of your process.

我们已经看到了什么是预处理器，以及如何安装。同时我们也看了一些流行的功能和一些缺陷。最后，我们了解了预处理器是如何使组织项目变得更容易的。因此，预处理器绝对可以成为您开发过程有用的部分。

