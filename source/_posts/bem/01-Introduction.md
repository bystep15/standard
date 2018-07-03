title: 01、介绍（Introduction）
categories: [理论, css, bem]
date: 2018/06/28 20:30:00
tags: [理论, css, bem]
---

[原文](http://getbem.com/introduction/)

On smaller brochure sites, how you organize your styles isn’t usually a big concern. You get in there, write some CSS, or maybe even some SASS. You compile it all into a single stylesheet with SASS’s production settings, and then you aggregate it to get all the stylesheets from modules into a nice tidy package.

在小型网站上，设计网站的样式表通常问题不大。这种情况下，写一些CSS，或一些SASS就可以实现想要的效果。使用SASS的生产配置编译，将相关的样式表合到一个压缩后的文件中即可。

However, when it comes to larger, more complex projects, how you organize your code is the key to efficiency in at least these three ways: it affects how long it takes you to write code, how much of that code you’ll have to write and how much loading your browser will have to do. This becomes especially important when you’re working with teams of themers, and when high performance is essential.

但是，当网站变得更大，项目更复杂时，需要从3个关键细节思考如何有效地组织代码：编写代码的时间、编写代码的数量和浏览器加载的大小。在团队合作中这3点会更重要，同时必须考虑代码的性能。

This is also true for long-term projects with legacy code (read ["How to Scale and Maintain Legacy CSS with Sass and SMACSS"](http://webuild.envato.com/blog/how-to-scale-and-maintain-legacy-css-with-sass-and-smacss/) — some nice SMACSS and BEM mixing in there).

对于项目中的历史遗留代码也是如此（请参阅[“如何使用Sass和SMACSS来扩展和维护历史遗留的CSS代码”](http://webuild.envato.com/blog/how-to-scale-and-maintain-legacy-css-with-sass-and-smacss/) - 里面包含一些混合使用SMACSS和BEM的优秀案例）。

## 方法（Methodologies）

There are plenty of [methodologies](https://github.com/ikkou/awesome-css#architecture) out there aiming to reduce the CSS footprint, organize cooperation among programmers and maintain large CSS codebases. This is obvious in large projects like Twitter, Facebook and [Github](http://markdotto.com/2014/07/23/githubs-css/#two-bundles), but other projects often grow into some “Huge CSS file” state pretty quickly.

目前有很多[方法](https://github.com/ikkou/awesome-css#architecture)可以减少CSS的体积，处理工程师的合作问题以及维护大型的CSS代码库。这在Twitter，Facebook和[Github](http://markdotto.com/2014/07/23/githubs-css/#two-bundles)等公司的大型项目上表现明显，但一些其他项目的CSS的体积往往迅速膨胀。

#### [OOCSS](http://oocss.org/)

Separating container and content with CSS “objects”

使用CSS“对象”分离容器和内容

#### [SMACSS](http://smacss.com/)

Style-guide to write your CSS with five categories for CSS rules

通过五个CSS规范为您提供CSS的样式书写标准

#### [SUITCSS](http://suitcss.github.io/)

Structured class names and meaningful hyphens

结构化的类名和有意义的连字符

#### [Atomic](http://github.com/nemophrost/atomic-css)

Breaking down styles into atomic, or indivisible, pieces

将样式分解为最基本的，不可分割的片段

## 为什么选择BEM（Why BEM over the others?）

No matter what methodology you choose to use in your projects, you will benefit from the advantages of more structured CSS and UI. Some styles are less strict and more flexible, while others are easier to understand and adapt in a team.

无论在您的项目中选择使用哪种方法，您都会获得结构化CSS和UI带来的优势。有的方法约束宽松、格式灵活，有的方法更容易理解、更适应团队。

> The reason I choose BEM over other methodologies comes down to this: it is less confusing than the other methods (i.e. SMACSS) but still provides us the good architecture we want (i.e. OOCSS) and with a recognizable terminology.
> 
> Mark McDonnell, [Maintainable CSS with BEM](http://www.integralist.co.uk/posts/bem.html#4)


> 相比其他方法，选择BEM的原因是：它不会像其他方法有那么多令人困惑的地方（比如SMACSS），同时用一种易识别的术语满足了我们想要的架构（比如OOCSS)。
>
> Mark McDonnell, [通过BEM编写可维护性的CSS](http://www.integralist.co.uk/posts/bem.html#4)

## 块，元素和修饰符（Blocks, Elements and Modifiers）

You will not be surprised to hear that BEM is an abbreviation of the key elements of the methodology — Block, Element and Modifier. BEM’s strict naming rules can be found [here](/standard/2018/06/28/02、命名（naming）.html).

BEM是块(block)，元素(element)和修饰符(modifier)的缩写，可以在[这里](/standard/2018/06/28/02、命名（naming）.html)查看详细的BEM命名规则。

### 块（Block）

Standalone entity that is meaningful on its own.

块是独立的实体，本身有意义。

##### 范例（Examples）

`header`, `container`, `menu`, `checkbox`, `input`

### 元素（Element）

A part of a block that has no standalone meaning and is semantically tied to its block.

元素是块的组成部分，没有独立的意义，并且在语义上与它对应的块关联。

##### 范例（Examples）

`menu item`, `list item`, `checkbox caption`, `header title`

### 修饰符（Modifier）

A flag on a block or element. Use them to change appearance or behavior.

块或元素的标记。可以使用它们来改变块或元素的样式和行为。

##### 范例（Examples）

`disabled`, `highlighted`, `checked`, `fixed`, `size big`, `color yellow`

![](/standard/media/bem/github_captions-1.jpg)

## 测试（Under the hood）

Let’s look how one particular element on a page can be implemented in BEM. We will take `button` from [GitHub](http://primercss.io/buttons/):

接下来看看如何使用BEM实现页面上的一个特定元素。以[Github](http://primercss.io/buttons/)上的`button`为例：

![](/standard/media/bem/github_buttons-1.jpg)

We can have a normal button for usual cases, and two more states for different ones. Because we style blocks by class selectors with BEM, we can implement them using any tags we want (`button`, `a` or even `div`). The naming rules tell us to use `block--modifier-value` syntax.

一般情况下会使用正常样式的按钮，有时候也需要其他两种状态。因为使用BEM的类选择器对块应用样式，可以应用于任何想要使用的标签（`button`,`a`或`div`），命名规则使用`block--modifier-value`语法。

#### HTML
```html
<button class="button">
    Normal button
</button>
<button class="button button--state-success">
    Success button
</button>
<button class="button button--state-danger">
    Danger button
</button>
```
#### CSS

```css
.button {
    display: inline-block;
    border-radius: 3px;
    padding: 7px 12px;
    border: 1px solid #D5D5D5;
    background-image: linear-gradient(#EEE, #DDD);
    font: 700 13px/18px Helvetica, arial;
}
.button--state-success {
    color: #FFF;
    background: #569E3D linear-gradient(#79D858, #569E3D) repeat-x;
    border-color: #4A993E;
}
.button--state-danger {
    color: #900;
}
```

## 优势（Benefits）

#### 模块化（Modularity）

Block styles are never dependent on other elements on a page, so you will never experience [problems from cascading](http://www.phase2technology.com/blog/used-and-abused-css-inheritance-and-our-misuse-of-the-cascade/).

块的样式不依赖于页面上的其他元素，所以您不会遇到[样式层叠](http://www.phase2technology.com/blog/used-and-abused-css-inheritance-and-our-misuse-of-the-cascade/)的问题。

You also get the ability to transfer blocks from your finished projects to new ones.

还可以在新项目中使用原先完成的项目中的块。

#### 可复用（Reusability）

Composing independent blocks in different ways, and reusing them intelligently, reduces the amount of CSS code that you will have to maintain.

通过不同的方式组合独立块，并合理的重用它们，可以有效地减少需要维护的CSS代码量。

With a set of style guidelines in place, you can build a library of blocks, making your CSS super effective.

可以建立一个基于块的标准样式库，使CSS变得更高效。

#### 结构化（Structure）

BEM methodology gives your CSS code a solid structure that remains simple and easy to understand.

BEM方法可以保持CSS代码简单易懂，并有非常稳定的结构。

## 未来阅读资料（Further Reading）

* [简而言之，为什么选择BEM？（‘Why BEM?’ in a nutshell）](http://blog.decaf.de/2015/06/24/why-bem-in-a-nutshell/)
* [MindBEMding](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/) — 您的最佳BEM语法（getting your head ’round BEM syntax）
* [CSS标准（CSS guidelines）](http://cssguidelin.es/#bem-like-naming)
* [小型项目中的BEM方法（BEM methodology for small projects）](http://www.smashingmagazine.com/2014/07/17/bem-methodology-for-small-projects/)
* [BEM It! for Brandwatch](http://www.slideshare.net/MaxShirshin/bem-it-for-brandwatch)
* [使用和滥用（Used and Abused）](http://www.phase2technology.com/blog/used-and-abused-css-inheritance-and-our-misuse-of-the-cascade/) — 我们对CSS继承和层叠的误用（CSS Inheritance and Our Misuse of the Cascade.）
* [空间中的对象（Objects in Space）](https://medium.com/objects-in-space/objects-in-space-f6f404727) — （使用SMACSS和BEM开发模块化SASS样式的指南）A style-guide for modular SASS development using SMACSS and BEM
* [如何使用Sass和SMACSS扩展和维护旧版的CSS（How to Scale and Maintain Legacy CSS with Sass and SMACSS）](http://webuild.envato.com/blog/how-to-scale-and-maintain-legacy-css-with-sass-and-smacss/)
* [使用BEM和Sass构建“My Health Skills”模块（Building a modular My Health Skills with BEM and Sass）](http://www.bluegg.co.uk/building-my-health-skills-part-3/)
* [构建“My Health Skills- ”第三部分（Building My Health Skills — Part 3）](http://www.bluegg.co.uk/building-my-health-skills-part-3/)

## 案例分析（Case study）

We hope to write "How to migrate an existing project to BEM" soon. In the meantime you can watch this nice presentation by Nicole Sullivan — "[CSS preprocessor performance](http://www.youtube.com/watch?v=0NDyopLKE1w)". She gives a very good overview of the problems she encounters in the majority of websites and offers ways to track them down and handle them.

我们会尽快撰写“如何将现有项目迁移到BEM”说明。与此同时，您可以观看Nicole Sullivan的精彩演讲 - “[高效的CSS预处理器](http://www.youtube.com/watch?v=0NDyopLKE1w)”。她很好地概述了大多数网站中遇到的问题，并提供了追踪和处理这些问题的方法。

