# 对CSS的规则进行分类（Categorizing CSS Rules）

[原文](https://smacss.com/book/categorizing)

Every project needs some organization. Throwing every new style you create onto the end of a single file would make finding things more difficult and would be very confusing for anybody else working on the project. Of course, you likely have some organization in place already. Hopefully, what you read among these pages will highlight what works with your existing process and, if I’m lucky, you will see new ways in which you can improve your process.

每个项目都需要有一些规范。 如果把您创造的每一种新的样式放到单个文件的最后的话，会让查找相关内容变得更加复杂，并且对于从事这个项目的其他人来说，一些都会变得很混乱。当然,你可能已经有了一些规范。如果我幸运的话，在您阅读这些内容时，当与您现有工作内容相比时，你会看到可以用来改善你的流程的新方法。

How do you decide whether to use ID selectors, or class selectors, or any number of selectors that are at your disposal? How do you decide which elements should get the styling magic you wish to bestow upon it? How do you make it easy to understand how your site and your styles are organized?

您是如何决定是使用ID选择器，还是类选择器，或是其他任何数量的您可以选择的选择器呢？ 你又是如何决定对于哪些元素赋予您添加的样式呢？那您又是如何让您的网站和您的编写的样式结构更清晰易懂呢？

At the very core of SMACSS is categorization. By categorizing CSS rules, we begin to see patterns and can define better practices around each of these patterns.

在SMACSS中，非常核心的一点就是分类。通过对CSS的规则进行分类，我们可以得到对应的模式并可以对这些模式的定义有更好的了解。

There are five types of categories:

1. Base
2. Layout
3. Module
4. State
5. Theme

这里主要包括五种类型:

1. 基类
2. 布局
3. 模块
4. 状态
5. 主题

We often find ourselves mixing styles across each of these categories. If we are more aware of what we are trying to style, we can avoid the complexity that comes from intertwining these rules.

我们会发现，当我们编写样式时，经常会混用以上的规则。如果我们更了解我们想要的样式，我们就可以避免因为混用这些规则所带来的复杂性。

Each category has certain guidelines that apply to it. This somewhat succinct separation allows us to ask ourselves questions during the development process. How are we going to code things and why are we going to code them that way?

每个类别都有其适用的一些准则。 这种简洁的分离，多多少少会让我们可以在开发过程中自问： 我们如何编写代码，为什么要这样编写代码？

Much of the purpose of categorizing things is to codify patterns—things that repeat themselves within our design. Repetition results in less code, easier maintenance, and greater consistency in the user experience. These are all wins. Exceptions to the rule can be advantageous but they should be justified.

对事物进行分类的很大一部分目的是对模式进行编码 - 在我们的设计的东西里，代码重复量越少，维护越容易，用户体验也更一致。 这些都是很好的结果。 也许有些会有一些例外，但这些例外是有一定道理的。

Base rules are the defaults. They are almost exclusively single element selectors but it could include attribute selectors, pseudo-class selectors, child selectors or sibling selectors. Essentially, a base style says that wherever this element is on the page, it should look like this.

基本规则是默认的。 它们几乎都是单个元素选择器，或者属性选择器，伪类选择器，子选择器或兄弟选择器。 总的来说，一个基本的样式就是无论这个元素在哪个页面上，它的表现形式都应该是一样的。

基本样式的例子（Examples of Base Styles）

```
html, body, form { margin: 0; padding: 0; }
input[type=text] { border: 1px solid #999; }
a { color: #039; }
a:hover { color: #03C; }
```

Layout rules divide the page into sections. Layouts hold one or more modules together.

布局规则将页面分成几个部分。布局通常将一个或多个模块放在一起。

Modules are the reusable, modular parts of our design. They are the callouts, the sidebar sections, the product lists and so on.

Modules（模块）是我们设计的可重复使用的模块化部分。 它们通常是一些标注，侧边栏，产品列表等等。

State rules are ways to describe how our modules or layouts will look when in a particular state. Is it hidden or expanded? Is it active or inactive? They are about describing how a module or layout looks on screens that are smaller or bigger. They are also about describing how a module might look in different views like the home page or the inside page.

状态规则是描述我们的模块或布局在特定状态下的外观的方式。它需要隐藏还是扩展？是活跃还是不活跃？ 他们是描述如何在更小或更大的屏幕上合理的显示模块或布局的规则。同时他们也是描述一个模块如何在不同的视图，如主页或内部页面里显示的规则。

Finally, Theme rules are similar to state rules in that they describe how modules or layouts might look. Most sites don’t require a layer of theming but it is good to be aware of it.

最后，主题规则与状态规则类似，它们描述了模块或布局的外观。 大多数网站不需要涉及到主题层次，但如果能意识到这一点，那将会是极好的。

## 命名规则（Naming Rules）

By separating rules into the five categories, naming convention is beneficial for immediately understanding which category a particular style belongs to and its role within the overall scope of the page. On large projects, it is more likely to have styles broken up across multiple files. In these cases, naming convention also makes it easier to find which file a style belongs to.

通过将规则分成五个类别，命名约定有助于立即理解特定的样式属于哪个类别，以及它在页面整体范围内所起到的作用。在大型项目中，更有可能在多个文件中分离样式。在这些情况下，命名约定也可以更容易地找到一个样式属于哪个文件。

I like to use a prefix to differentiate between Layout, State, and Module rules. For Layout, I use `l-` but `layout-` would work just as well. Using prefixes like `grid-` also provide enough clarity to separate layout styles from other styles. For State rules, I like `is-` as in `is-hidden` or `is-collapsed`. This helps describe things in a very readable way.

我喜欢使用前缀来区分布局规则，状态规则和模块规则。对于布局规则，我通常使用`l-`但是`layout-`也可以使用。 使用`grid-`等前缀也足以将布局样式与其他样式分离开。对于状态规则，我喜欢用`is-`前缀，就像`is-hidden`或者`is-collapsed`。 这有助于以一种非常可读的方式描述事物。

Modules are going to be the bulk of any project. As a result, having every module start with a prefix like `.module-` would be needlessly verbose. Modules just use the name of the module itself.

模块将成为任何项目的主体。 因此，让每个模块都以一个像`.module-`这样的前缀开头是没有必要的。 模块只是使用模块本身的名称。

举例（Example classes）

```
/* Example Module */
.example { }

/* Callout Module */
.callout { }

/* Callout Module with State */
.callout.is-collapsed { }

/* Form field module */
.field { }

/* Inline layout  */
.l-inline { }

```

Related elements within a module use the base name as a prefix. On this site, code examples use `.exm` and the captions use `.exm-caption`. I can instantly look at the caption class and understand that it is related to the code examples and where I can find the styles for that.

模块中的相关元素使用基本名称作为前缀。在这个网站上，代码示例使用`.exm`，标题使用`.exm-caption`。 我可以立即查看标题类，并了解它与代码示例有关，并且可以在其中找到相应的样式。

Modules that are a variation on another module should also use the base module name as a prefix. Sub-classing is covered in more detail in the Module Rules chapter.

基于另一个模块的模块也应该使用基本模块名称作为前缀。 子模块将会在模块规则一章中有更详细的介绍。

This naming convention will be used throughout these pages. Like most other things that I have outlined here, don’t feel like you have to stick to these guidelines rigidly. Have a convention, document it, and stick to it.

这个命名约定将会伴随着所有的页面。像我在这里概述的大多其他事情一样，不要拘泥于这些指导原则。 记住，我们有一个原则，记录内容，并坚持下去。

