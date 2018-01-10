# 介绍（Introduction）

[原文](https://smacss.com/book/)

I have long lost count of how many web sites I’ve built. You would think after having built a few hundred of them I would have discovered the “one true way” of doing it. I don’t think there is one true way. What I have discovered are techniques that can keep CSS more organized and more structured, leading to code that is easier to build and easier to maintain.

我已经忘了我写过多少网站了。 也许您可能会问，在建立了几百个网站以后，我是否发现了一个制作网站“绝对正确的方法”? 其实，我不认为有这样一个方法。 但是，我发现一个可以使CSS更有组织，更结构性的技术，利用这个技术，会使代码更容易构建，更易于维护。

I have been analyzing my process (and the process of those around me) and figuring out how best to structure code for projects on a larger scale. The concepts were vaguely there with the smaller sites that I had worked on but have become more concrete as a result of working on increasingly complex projects. Small sites don’t often hit the same pain points as larger sites or working with larger teams; small sites aren’t as complex and don’t change as often. However, what I describe in these pages is an approach that works equally well for sites small and large.

我一直在分析我的流程（以及我身边的流程），并研究如何更好地为大型项目构建代码。 这些概念隐约与我曾经工作过的较小的网站有关，但是由于日益复杂的项目工作而变得更加具体。 小型网站不会像大型网站那样经常遇到同样的痛点，或者与大型团队合作; 小型网站不那么复杂，不经常改变。 但是，我在这些页面中描述的方法对大小网站来说同样适用。

SMACSS (pronounced “smacks”) is more style guide than rigid framework. There is no library within here for you to download or install. SMACSS is a way to examine your design process and as a way to fit those rigid frameworks into a flexible thought process. It is an attempt to document a consistent approach to site development when using CSS. And really, who isn’t building a site with CSS these days?! Feel free to take this in its entirety or use only the parts that work best for you. Or don’t use it at all. I understand that this won’t be everybody’s cup of tea. When it comes to web development, the answer to most questions is “it depends”.

SMACSS（发音为“smacks”）相比于死板的框架，更具风格性指导的特点。 这里没有相关的库供您下载或安装。 SMACSS是检查您设计过程的一种方式，也是将这些僵化的框架纳入灵活的思维过程的一种方式。 这是一个尝试记录在网站开发过程中对CSS一致性使用的方法。 而且，说实话，这时代谁不用CSS构建网站？ 您可以选择阅读这些内容的全部，或者只选择最适合您的部分。 或者根本不使用它。 我明白，这不会符合所有人的看法。毕竟当谈到网站开发时，大多数问题的答案是“依据情况而定”。

## 灵感（Inspiration）

In trying to learn more about what does and doesn't work in maintaining larger projects, I looked at how others were trying to solve similar problems. Nicole Sullivan's [Object Oriented CSS](http://oocss.org/), Jina's presentations on [CSS Workflow](https://vimeo.com/15982903), Natalie Downe's talk on [Practical, maintainable CSS](http://blog.natbat.net/post/46613977728/practical-maintainable-css), and, lastly, Jeremy Keith's [Pattern Primer](https://adactio.com/journal/5028) were large influences on what was to become SMACSS.

在学习更多关于维护更大的项目中哪些应该保留哪些不该保留的过程中，我观察了其他人解决类似问题的方法。 Nicole Sullivan的[面向对象的CSS](http://oocss.org/)，Jina关于[CSS工作流程](https://vimeo.com/15982903)的演讲，Natalie Downe关于[实用，可维护性的CSS](http://blog.natbat.net/post/46613977728/practical-maintainable-css)的讲说，以及Jeremy Keith的[模式入门](https://adactio.com/journal/5028)都对我编写SMACSS的内容产生了巨大的影响。

## 以下哪些内容？（What’s in here?）

My thoughts have been compartmentalized around a number of topics related to CSS architecture. Each thought is detailed in its own section. Read the sections in sequence or out of order or pick and choose what seems most relevant to you. It’s not 1000 pages of writing; the sections are relatively short and easy to digest.

我已经对CSS架构相关的一些主题进行了划分。 每个想法在各自的部分中都有详细的介绍。 您可以选择按顺序阅读或不按顺序阅读，亦或是挑选看起来最相关的东西。 这里没有1000页的内容让您抓狂;恰恰相反，每个部分的内容都相对较短，易于理解。

Now get started and dive in!

现在，让我开始并深入学习吧！



