# 格式化代码（Formatting Code）

[原文](https://smacss.com/book/formatting)

Everybody has their own way. The tools and techniques that you use are ones that you have tried either through trial and error or you have tried what you heard works for other people. When I first got into development, I used Dreamweaver. It had plenty of features and allowed me to build static HTML sites quickly and efficiently. After seeing a co-worker using Ultraedit and seeing how fast he was able to get work done, I started to learn it as a way of complementing my existing tool set. The same has occurred with the way I code. I will see a technique or style that someone else uses and I will assimilate those techniques into my own way of working.

每个人都有自己的方式。您使用的工具和技术是您经过尝试和试错后的选择，或是其他人向您推荐的作品。当我第一次开发时，我使用的是Dreamweaver。它有很多功能，并允许我快速有效地建立静态HTML网站。在看到一个使用Ultraedit的同事并看到他能够完成工作的速度有多快之后，我开始学习Ultraedit，并将其作为补充现有工具的一种方式。我编码的过程也一样。我会看其他人使用的技术或者样式，并选择自己喜欢的技术并将其融入我自己的工作方式。

This section, Formatting Code, is a brief look at how I code my work and do so in a way that seems to work well for others having to continue working on my code.

这一章节，格式化代码，简要介绍了如何对代码进行编码，和其他人的代码对我工作的帮助。

## 单行方式与多行方式（Single line versus multiple lines）

For many years, I have coded my CSS using the [single line approach](http://orderedlist.com/resources/html-css/single-line-css/). This means that all of the properties for a given rule set are declared on the same line. This allows for quick scanning of the selectors along the left. Being able to scan selectors has traditionally been more important to me than seeing properties nicely lined up. Up until just a couple years ago, the list of properties assigned to a rule set were quite small; it would be unusual to have more than a handful. Therefore, I could find the selector I wanted and all of the properties would be visible on the screen.

多年来，我一直使用[单行方法](http://orderedlist.com/resources/html-css/single-line-css/)编写CSS代码。这意味着给定规则集的所有属性都会在同一行中声明。这样可以快速扫描左侧的选择器。 对于我来说，观察选择器的能力一直比排列的整齐程度更重要。知道几年前，既有的规则集的属性列表都非常短，并且有一小部分是不常用的。因此，我可以方便地找到我想要的选择器，并且所有的属性都可以在屏幕上看到。

With CSS3—and the myriad of vendor-specific prefixes that come with it—things can get out of hand rather quickly. Between that and working with a larger team, it was easier for everybody to have each property/value pair on its own line.

但是，自从有了CSS3以及随之而来的众多供应商特定的前缀，事情很快就失去控制。此时，与一个更大的团队合作成为必然，并且每行内容都拥有键值对也会减少消耗的时间。

CSS3 with the plethora of vendor-prefixed properties can be too much to read easily if all on one line.

如果过多的供应商前缀的CSS3属性堆积在一行中，那就太不容易阅读了。

```
.module {
    display: block;
    height: 200px;
    width: 200px;
    float: left;
    position: relative;

    border: 1px solid #333;
    -moz-border-radius: 10px;
    -webkit-border-radius: 10px;
    border-radius: 10px;

    -moz-box-shadow: 10px 10px 5px #888;
    -webkit-box-shadow: 10px 10px 5px #888;
    box-shadow: 10px 10px 5px #888;

    font-size: 12px;
    text-transform: uppercase;
}
```

In the example, there are 11 properties declared and we could easily have a half-dozen more if we added another feature or two to our module. Having these all on one line would leave the first handful of properties visible on the screen and we would be left scrolling to the right to uncover the rest of the properties. This makes it hard to scan the document and see what properties have been defined.

在这个例子中，我们声明了11个属性，如果我们在模块中添加了另外一个或两个属性，我们得一次添加好几个。如果将所有这些全部放在一行上，将会在屏幕上显示出第一批属性，然后我们将向左滚动以显示剩下的属性。这使得很难查看文档中已定义的属性。

There are a few other minor things to note with the example:

* There is a space after the colon.
* Four spaces before each declaration (no tabs).
* Properties are grouped by type.
* Opening bracket on the same line as the rule set.
* Colour declarations use the short form.

这个例子还有一些其他小的地方需要注意：

* 冒号后面留一个空格。
* 每个生命前面留四个空格（无标签）。
* 属性按类型分组。
* 在规则集的上下两行加括号。
* 颜色生命使用简写形式。

These are all preferential and I will not begrudge you for using a completely different approach. This is just what I have found that feels natural and makes the most sense to me.

这些都是有好处的，我认为您使用一种不同的方法是不可取的。因为这是我自然而然发现的，并认为更有意义的。

## 分组属性（Grouping Properties）

Some people organize alphabetically, others don’t organize at all, and others may use some other arbitrary system. I fall in this last category. It's not completely arbitrary, mind you. I would describe it as ordering from most important to least important but what is important when it comes to declaring styles on an element?

有些人按字母顺序进行排序，有些人根本不排序，其他人可能会使用一些其他的方式进行排序。而我属于最后一类。我要声明的是，这不是完全武断的。因为我会将内容按照最重要到最不重要的顺序进行排序，但是当涉及到在元素上声明样式时，什么是重要的呢？

I organize in the following order:

1. Box
2. Border
3. Background
4. Text
5. Other

我组织了以下的顺序：

1. 盒子
2. 边框
3. 背景
4. 文本
5. 其他

Box includes any property that affects the display and position of the box such as `display`, `float`, `position`, `left`, `top`, `height`, `width` and so on. These are most important to me because they affect the flow of the rest of the document.

盒子包括可以影响盒子的显示和位置的任何属性，如`display`, `float`, `position`, `left`, `top`, `height`, `width`等等。这些对我来说是最重要的，因为它们会影响文档的其他部分的布局。

Border includes `border`, the oft-unused `border-image`, and `border-radius`.

边框包括`border`，还有不常用的`border-image`以及`border-radius`。

Background comes next. With the advent of CSS3 gradients, background declarations can actually become quite verbose. Once again, vendor prefixes just compound the issue.

接下来是背景。随着CSS3渐变的到来，背景的声明可能会变得非常冗长。同时，供应商的前缀也会增加项目的复杂度。

CSS3声明的多背景图（Multiple backgrounds with CSS3 declarations.）

```
background-color: #6d695c;
background-image: url("/img/argyle.png");
background-image:
  repeating-linear-gradient(-30deg, rgba(255,255,255,.1), rgba(255,255,255,.1) 1px, transparent 1px, transparent 60px),
  repeating-linear-gradient(30deg, rgba(255,255,255,.1), rgba(255,255,255,.1) 1px, transparent 1px, transparent 60px),
  linear-gradient(30deg, rgba(0,0,0,.1) 25%, transparent 25%, transparent 75%, rgba(0,0,0,.1) 75%, rgba(0,0,0,.1)),
  linear-gradient(-30deg, rgba(0,0,0,.1) 25%, transparent 25%, transparent 75%, rgba(0,0,0,.1) 75%, rgba(0,0,0,.1));
background-size: 70px 120px;
```

Complex patterns are possible with CSS3 gradients but create for lengthy background declarations, and the example doesn't even include CSS3 prefixes. Just imagine how long this declaration would be if it did!

复杂的情况可能包括CSS3渐变。但请注意，在创建这个冗长的背景声明时，该示例甚至都不包括CSS3前缀。 试想一下，如果加上前缀声明，这些内容得多长！

Text declarations include `font-family`, `font-size`, `text-transform`, `letter-spacing` and any other CSS properties that affect the display of the type.

文本声明包括`font-family`, `font-size`, `text-transform`, `letter-spacing`和任何其他可以影响样式的CSS属性。

Anything that doesn’t fall into any of the above categories gets added to the end.

任何不属于上述任何类别的东西都会被添加到最后的其他部分中。

## 颜色声明（Colour Declarations）

This may seem like a silly thing to even mention but I have seen different developers do different things. Some like using keywords like `black` and `white` but I have always tried to stick to either the 3 digit or 6 digit hex format wherever possible. `#000` and `#FFF` are shorter, albeit barely, then their keyword counterparts. Likewise, I wouldn’t use `rgb` or `hsl`, since the hex form is shorter. Of course, `rgba` and `hsla`have no hex form and they would get used.

这可能看起来有点蠢，但我已经看到不同的开发人员使用这种方式做了不同的事情。有些人喜欢用`black`或者`white`这样的关键字，但是我一直试图坚持使用3位或6位的格式。＃000和#FFF虽然比较繁琐，但是与关键字相比却很短。同样，我也不会使用rgb或hsl，因为它们没有十六进制的格式短。当然，rgba和hslahave没有十六进制形式，所以我们可以采用它们。

