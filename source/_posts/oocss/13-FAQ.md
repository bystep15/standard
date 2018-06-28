title: 13、常见问题（FAQ）
categories: [理论, css, oocss]
tags: [理论, css, oocss]
date: 2018/06/28 14:30:00
---


[原文](https://github.com/stubbornella/oocss/wiki/FAQ)

Whoa, you have lots of questions! I'd better start recording the answers if I want to scale better.

哇，看来你有很多问题！ 如果我想把内容描述的更好，我最好开始记录答案。

## OOCSS中“对象”具体指什么？（What is meant by an "object" in OOCSS?）

In keeping with the OO metaphor, an object is analogous with an instance of Java or PHP class, for example (though the [granularity is different!](http://www.stubbornella.org/content/2010/06/21/css-granularity-architecture/))

为了保持与面向对象中的概念一致，对象可以类比为Java或PHP的类一个实例（尽管[粒度不同](http://www.stubbornella.org/content/2010/06/21/css-granularity-architecture/)！）

A CSS object consists of four things:
- HTML, which can be one or more nodes of the DOM,
- CSS declarations about the style of those nodes all of which begin with the class name of the wrapper node
- Components like background images and sprites required for display, and
- JavaScript behaviors, listeners, or methods associated with the object.

一个CSS对象由以下四个部分组成：
- HTML，表示DOM的一个或多个子节点。
- 所有以容器节点的类名为前缀的CSS样式声明
- 需要显示的背景图像和精灵等的组件
- JavaScript功能，监听器和与对象关联的方法。

This can be confusing because each CSS class is not necessarily an object in its own right, but can be a property of a wrapper class.

令人困惑的是，每个CSS类本身不一定是一个对象，但可以是一个容器类的属性。

For example:

例如：

```html
<div class="mod">
    <div class="inner">
         <div class="hd">Block Head</div>
         <div class="bd">Block Body</div>
         <div class="ft">Block Foot</div>
    </div>
</div>
```

The object is a module, indicated by the class mod. It contains four property nodes (which cannot live independently from the module, including two required regions, inner and body, and two optional regions, head and foot.

该对象是一个模块，由类mod来表示。 它包含四个属性节点（这些节点不能脱离于模块，包括两个必要的区域，内部（inner）和正文（body），以及两个可选区域，头部（head）和脚部（foot）。

## 面向对象的CSS是如何提高性能的？（How does OOCSS improve performance?）

The performance benefits of OOCSS are twofold:

1. Heavy reuse of CSS code, so less CSS code needed, which means:
    1. Smaller files, hence faster transfers
    2. A bigger percentage of the CSS code needed on most pages of your site is likely to be reused and possibly cached by the browser

2. To a lesser degree, fewer repaints and layout calculations on the part of the browser.  
    On a single page, the more CSS rules are reused, the less time the rendering engine spends calculating "computed values"

OOCSS从两个方面优化性能：

1. CSS代码复用，所需的CSS代码数量更少，这意味着：
    1. 文件体积更小，可以更快的传输
    2. 网站大多数页面上会重用大部分CSS代码，浏览器可能会对其进行缓存

2. 减少计算，浏览器会减少重绘和布局计算。
    在单个页面上，CSS规则被重用的越多，渲染引擎花费“计算值”的时间越少。

## 可以用ID来描述样式吗？（Should I use IDs to style my content?）

There are two reasons for not using ID's to style content:
1. They mess up specificity because they are too strong (the most important reason)
2. They are unique identifiers, which makes components built with them something like singletons, not reusable on the same page


有两个原因来说明不适合使用ID来描述样式：
1. 因为它们的功能太强大了，如果使用会混淆了ID的特异性（这是最主要的原因）
2. 它们是唯一的标识符，它使得构建的组件像单件一样，不能在同一页面上重用

When you reuse an object in the same page (or on the same site if the cache is working properly), it is a performance "freebie".  Styling using IDs makes it impossible to use the same element twice on the same page. @cgriego (twitter) compared it to singletons, which sounds accurate to me.  There may be cases where you want to style using an ID, like header menus that are very specific, in this case you can use an ID to sandbox the particular element and be sure that the code written for it doesn't impact the rest of the site. Think carefully before you choose an ID over a class, it is really hard to predict what people will do with HTML built from your CSS as the site evolves. If you have a choice, leave things as flexible as possible.

当一个页面中重用一个对象时（或者同站点的缓存生效时），会带来一定的性能优化。如果使用ID选择器，那么在同一页面上相同的元素不能出现两次。@cgriego （推特）将其比作单例，这种说法听起来是准确的。在某些情况下，可能需要使用一个ID的样式，比如非常特殊的标题菜单，在这种情况下，你可以使用一个ID来指定对应的元素，并确保为它写的代码不会影响网站的其余部分。慎重使用ID对类进行覆盖，随着网站的发展，很难预测人们如何使用跟CSS相关的HTML。所以选择的原则是，尽可能的保持可复用性和灵活性。

I removed the ids from head, body, and foot in my template. Someone could have multiple main content areas.  Multiple site headers and footers are more difficult to imagine, but I bet there is a designer who can dream up something like that, so the IDs needed to disappear. 

我已经从模板中的头部，主体和尾部删除了ID。 也许存在多个主要内容区域的情况，那样对于多站点的页眉和页脚的数量是更难以想象的，但我敢打赌，肯定有设计师想过这样的事情，所以ID属性在这里不应出现。

On the other hand, IDs are great for linking and JS hooks.  Put them in the HTML, just don't use them for styles.

换句话说，ID对于链接和JS的钩子来说是个不错的选择。只是将它们放在HTML里面，但不要在样式中使用它们。

## 设计师能编写OOCSS吗？（Designers can't code OOCSS, can they?）

Yes, designers instinctively understand objects, it is much more concrete than the way most people are currently coding CSS --layers of exceptions (think, there was an old lady who swallowed a fly). In fact, they love OOCSS for two reasons.  

1. It allows them to ramp up a lot faster when creating complex high traffic sites. They don't have to bother with understanding the structures until they are reasonably competent and comfortable with basic syntax.
2. When learning CSS, they never have to create the ugly "hello world!" website.  Designers care very much that their work is beautiful.  If they have to make something ugly, even for the sake of learning, they will very quickly get frustrated and annoyed.  OO-CSS allows their work to be beautiful at each stage of the learning process. 

能，设计师天生理解对象，这种方式比目前大多数编写CSS的方式更具体——当然会存在例外。实际上设计师喜欢OOCSS主要出于两个原因。

1. 这使得他们可以更快的创建复杂的高流量网站。在正确、开心的理解基本语法之前，不必费心地去理解结构。
2. 在学习CSS时，他们永远不必创建无聊的“hello world！”网站。设计师非常在乎他们网站的优美程度。如果他们不得不为了学习而做出丑陋的事情，他们很快就会感到沮丧和烦恼。而OOCSS可以让他们在学习过程的每个阶段都感到优美。

Designers are smart.  We need to give them credit. They may speak a different, non-engineering language, but often geeky language excludes people in a way that is kind of ugly. We can do better than that.

永远要记住，设计师都是很聪明的。我们应当给予他们信任。他们也许会有一些非编程语言相关的表达，但通常人们对于编写不规范的代码都会感到厌烦。所以我们可以，也应该做得更好。

## 我是一名前端架构师，我应当如何向我的团队传达这些内容？（I'm a Front-end Architect, how do I teach this to my team?）

As the architect, you should write the structure object; set up how the rounded corner box is created, positions all the presentational elems for corners or other features, and deals with browser differences. Newbies write the skins for these modules (borders, colors, background images, etc).

由架构师来设计结构对象; 设计创建圆角的方式，定位所有角落或其他功能的表现元素，并处理浏览器兼容性。而新手为这些模块编写样式（边界，颜色，背景图像等）。

I built large scale sites (1000s of pages, millions of visitors) using the OO-CSS method. It scales well and, when done correctly, it means that the individual components a newbie would be working on are relatively predictable. Code review is easy because there are clear rules about acceptable ways to extend objects. This kind of feedback makes new developers productive really quickly.

我用面向对象的方法构建了一个大规模的站点（一千多个页面，百万级别的浏览者）。它的扩展性良好并且正确实现，这意味着一个新手编写的组件是相对可预测的。代码审查是很容易的，因为有明确的规则来扩展对象。 这种反馈使得新项目开发可以快速开展。

I managed a team of front end developers at FullSIX (a web marketing agency in France) who are among the most talented people I’ve ever worked with. At some point our success meant that we had far more work than we could handle. It is very hard to hire front-end experts (there is no school for this stuff!), so I started an [internal internship program where designers who were interested in exploring code](http://www.slideshare.net/stubbornella/object-oriented-css/57) (but had little to no previous experience) could come work as junior members of our team for one month.

* Week 1: They learned about semantics and built html from existing CSS. Learning to build new pages without writing more CSS, HTML syntax, multiple classes, validation, semantics, intro to code review, etc.
* Week 2: They built simple content objects (headings, lists, etc) for a week. Learning CSS syntax, how to extend objects, colors, % sizes for text, etc.
* Week 3: they were building block skins. Borders, colors, background images, basic positioning, sprites. They worked with an amazing senior developer who answered a ton of questions and really helped them scale the learning curve. He also happens to be a very talented code reviewer.
* Week 4: they were productive members of my team building skins that were production ready.

我在FullSIX（法国一家网络销售机构）管理一批前端开发人员，他们是我曾经共事过的最有才华的人。在某种程度上，我们的成功是因为我们的工作成果远高于我们的能力。 要聘请前端专家是非常困难的（学校里不会有这门课程），因此我开始了一个[内部实习计划](http://www.slideshare.net/stubbornella/object-oriented-css/57)，那些有兴趣研究代码（但以前几乎没有什么经验）的人可以作为初级工程师来我们团队工作一个月。

* 第一周：他们学习了语义化，并基于现有的CSS来构建了HTML。 学习用现有的CSS，HTML语法，多个类，有效性，语义化和代码审阅介绍来构建新的页面。
* 第二周：他们用这周的时间来构建简单的内容对象（标题，列表等）。并学习CSS语法，如何扩展对象，颜色，文本的百分比大小等。
* 第三周：他们来构建块级的样式。 边界，颜色，背景图像，基本定位，精灵图片。 他们和一个了不起的高级开发人员一起工作，并会解答他们很多问题，帮助他们扩展学习曲线。同时，他也会是一个非常有才华的代码审阅者。
* 第四周：他们已经成为我们团队高效的编写样式的工作人员。

Their code is live on a client website. It is as good as anything written by the senior developers, maybe better because they didn’t have to un-learn bad habits. :) 

他们的代码在线上的网站上使用，并且表现的跟有工作经验的高级开发者一样好，或者比他们更好，毕竟他们现在还没有学习一些坏习惯:)

## 起步：我应该如何用这些文件工作？（Getting Started: How do I work with these files?）

Three files, libraries.css (reset and fonts from yui), grids.css and template.css are ready, the others are still extremely unstable. 

1. [Download the whole project](http://github.com/stubbornella/oocss/downloads) via the download button.
2. Open template.html and save it as a new file.
3. Adapt the number and width of the columns by extending those objects. You only need one template for your site, even if you have pages with different columns, because the columns are objects like anything else. You can think of them as optional regions, you may have 0-n left columns.  See template docs for more information.
4. Use grids to break up any of the content areas into smaller chunks. See grids docs for more information.
5. Add content.  Hint: This should also be OO.
6. Copy and paste modules and talk bubbles, add content there too
7. Build new module styles based on "mod_skins.css"

libraries.css（基于YUI的重置和字体），grids.css和template.css已经是完成状态，其他的文件目前还不稳定。

1. 点击[下载整个项目](http://github.com/stubbornella/oocss/downloads)。
2. 打开template.html并将它另存为一个新的文件。
3. 通过扩展这些对象来调整列的数量和宽度。 即使您的网页具有不同的列数，您的网站也只需要一个模板，因为这些列数像其他的东西一样都是个对象。 您可以将它们视为可选区域，您可能有0-n个左列。有关更多信息，请参阅模板文档。
4. 使用网格将任何内容区域分解为更小的块。有关更多信息，请参阅网格文档。
5. 添加内容。提示，这部分也应该是面向对象的部分。
6. 复制和粘贴模块与对话框，并在此部分添加内容。
7. 基于"mod_skins.css"建造新的模块样式。

## 我应该如何将它们部署到一个线上的站点？（How do I deploy this on a live site?）

Keep in mind that the CSS is still evolving, I may change things based on feedback I'm receiving.

应当注意，这些CSS还在发展的过程中，我会基于收到的反馈来调整这些内容。

I've broken up the CSS files into modules like grids and template. On a real site you should remove unnecessary comments and reduce HTTP requests, or the site will be super slow.  This means you need to combine CSS files into one larger file.  I use nested comments, to keep the CSS organized.  Finally, run a CSS minifier as a part of the push/deployment process to remove stray comments.

我已经把CSS文件分解成像网格和模板这样的模块。 在一个真实的网站，你应该删除不必要的注释，并减少HTTP请求，否则该网站会变得超慢。 这意味着您需要将CSS文件合并成一个更大的文件。 我使用嵌套注释，以此来保持CSS的结构。 最后，运行CSS代码压缩作为推送/部署过程的一部分来移除注释。

## 我应该编辑这些文件，或者用我的样式表重写它们么？（Should I edit these files, or overwrite them with my own stylesheet?）

I wouldn't edit grids, template, or libraries.  A lot of testing has gone into getting those just right.  If you want to customize, think about extending the basic objects instead.

我不会编辑网格，模板或者库。许多测试已经证明这些内容处于正确的情况。 如果您想要自定义这些内容，请考虑扩展基本对象。

## 我不要粉色！那我应该如何修改content.css？（Pink is not my color! What do I do with content.css?）

You may well want to edit content.css. Go ahead, change colors, font sizes, capitalization.  Just keep in mind that this file is rapidly evolving and I don't have any docs yet to show you how to do it correctly.  I'm working on it, I promise.

您可以很容易的编辑content.css。您可以改变颜色，字体大小，大小写。请记住，这个文件正在迅速扩展，但目前我没有任何文档来告诉您如何正确地使用。我向您保证，我现在正在努力。

## 我需要在我的站点上多于六个标题（h1-h6），我应当如何添加呢？（I need more than six (h1-h6) headings on my site. How do I add more?）

If you want more than six heading styles, extend the heading objects by adding a new class.

如果您想要多于六个数量的标题样式，可以添加一个新类来扩展标题对象。

```css
.category {
  font-size: 108%;
  font-weight: normal;
  font-style: normal;
  text-transform: uppercase;
  color: #333;
}
```

What not to do:
而不是这样操作：

```css
#mySaleModule h2, 
#mySaleModule .h2 {
  font-size: 108%; 
  font-weight: normal;
  font-style: normal;
  text-transform: uppercase;
  color: #333;
}
```

## 我应该如何扩展一个对象？（How do I extend an object?）

If you want to extend an object, for example a 160px left column, rather than the default, you should add an additional class to the column.
如果您想扩展一个对象，例如一个不同于默认样式的160px的左边栏，您可以向列的类中添加一个额外的类。

```html
<div class="leftCol gMail"> ... </div>
```

If the default and extended widths of columns or pages don't match your site, you can extend the column to allow a custom width. 

如果列或页面的默认宽度和扩展宽度与您的站点不匹配，您可以扩展列以允许自定义宽度。

### 列（Columns）

`myColumn` extends column objects to allow for custom column widths.
您可以使用`myColumn`来扩展列以允许自定义宽度。

```css
.myColumn { width:400px; }
```

And the HTML
对于HTML

```html
<div class="leftCol myColumn"> ... </div>
```

Don't think of this as overwriting my classes, but rather extending the objects provided by the framework.  I give you columns, headings, and other objects.  You can extend those objects by adding another class that only specifies the differences between my base object and your implementation of the same. Mixins may be a good analogy here. 

不要认为这样做是覆盖掉了我原来的类，这是为扩展框架提供了扩展的对象。 我给您列，标题和其他对象。 您可以通过添加另一个类来扩展这些对象，该类只指定我的基础对象和您的具体要实现的样式之间的区别。 Mixins在这里可能是一个很好的比喻。

What not to do (because it will make it harder for you to upgrade to newer versions of my framework):

不要向下面这样做（因为当您这样做之后，用我这个框架更新时会带来极大的不便）：

```css
.leftCol{... custom css here ...}
```

## 对于无用的样式而言，我的站点永远都不会用到像160px宽的gmail样式的列，我可以移除它们么？（Unused Styles. My site will never have a 160px gmail-style column, is it ok to remove it?）

Sure.  Removing objects or extensions to those objects is perfectly reasonable. Just keep in mind that it is hard to imagine what HTML someone might build with your CSS when a site is still evolving. Premature optimization is a danger. 

当然。删除这些对象或这些对象的扩展是完全合理的。 但是请记住，很难确认在一个网站发展过程中，有没有人会用CSS来构建HTML。不成熟的优化是一个危险的行为。

## 为什么会有一个单一的模板？（Why have a single template?）

In object oriented CSS, an important goal is to have a single template from which all pages are built.  This eases CMS development because by having a single starting point all pages can be made into any other page. Users of the CMS do not have traps in which a page they have built cannot be morphed into a different page type.  Another goal of an OO template is to have each section (column, header, etc) control its own destiny.  Practically, that means that if you want to add a left column to the template, the only required action should be actually adding the column to the HTML.  You never want to write CSS in such a way that changes are required higher in the DOM tree in order to make child elements behave properly.  Looping through the dom is costly for CMS development. 

在面向对象的CSS中，一个重要的目标是为所有页面的模板构建一个单一的模板。 这样简化了CMS的开发，因为通过一个单一的起点，所有的页面可以被制作成任何其他页面。CMS的用户不会觉得他们构建的页面不能变化为不同的页面类型。面向对象的模板的另一个目标是让每个部分（列，标题等）可以自己控制自己的表现。 实际上，这意味着如果你想向模板添加左列，唯一需要的操作应该是向HTML中添加列。 如果只是为了让子元素的行为正确，您绝对不希望以这种方式编写CSS，因为在DOM树中修改需要更大的修改量。 在dom中循环对于CMS开发的代价实在太大了。

## 这是语义化么？我需要用`.formYellow` 或者`tinyBlueH2`来结尾我的类名么？（Is this semantic? Will I end up with classes like `.formYellow` or `tinyBlueH2`?）

OOCSS can be written in a semantic or non-semantic way, it is up to you to create modules like `errorMod` rather than `bigRedModule`. I've chosen class names with a few goals in mind (in no particular order).

- Brevity - every byte counts, so I kept classes as short as possible
- Clarity - expected behavior/style should be immediately obvious
- Semantic - what an object is matters more than what it looks like. How will it be used in the site?
- Generic - the name should be true for most sites. Overly specific names reduce the number of use cases or cause semantic classes to be used in a non-semantic way.  
- Screen - Different views might be provided by mobile or print stylesheets, however they override the default screen view, so the classes chosen are screen specific when there was a conflict. This simplifies development.

OOCSS可以通过语义化和非语义化的方式来编写，您可以用`errorMod`而不是`bigRedModule`来创建模块,这完全取决于您。我是基于下面的原则和类的目的来选择类的名称（没有特定的顺序）。

- 简洁 - 每一个字节的内容都是很重要的，所以我会将类尽可能的缩短
- 清晰 - 预期的表现/风格应该立马能显示出来
- 语义 - 对象是什么比看起来像什么更加重要。 并且它会如何在网站中使用？
- 通用 - 大多数网站的名称应该是正确的。 过于具体的名字减少了用例的数量或者导致语义类以非语义的方式被使用。
- 显示 - 移动端或者打印样式表可以提供不同的视图，但是它们会覆盖默认的屏幕视图，所以当出现冲突时，对于屏幕的不同，类也是有所不同。这样做会简化复杂度有利于发展。

The code and docs are a framework, an example of OOCSS. I can't predict what you are going to put in leftCol. I could call it navigation, but that may not be true for your site. Sometimes these important goals are in opposition to one another.  In those cases I've fallen back on pragmatism and made a judgement call. Nothing can replace a clever developer making the right choice in a given situation.

代码和文档是一个框架，OOCSS就是一个例子。 我无法预测你要把什么放在左边。 我姑且称之为导航，但是这样可能并能不适用您的网站。 有时这些重要的目标是对立的。 在这种情况下，我会基于了实际情况作出判断。 没有什么会比一个聪明的开发人员在给定的情况下做出正确的选择更重要了。

## 其他的库或者框架是怎样的？这个项目只跟YUI相关么？（What about other libraries/frameworks? Does this only work with YUI?）

In an ecosystem with a lot of frameworks and libraries, YUI stands out as an example of professionalism and scalability. I compare myself to them because I am continually impressed by the quality of their code and documentation. OOCSS isn't really a framework, though I'm creating one here as an example, but a way of writing scalable, sane, maintainable CSS. Maybe the best analogy is a new language. Ultimately, it is JavaScript library agnostic and I hope to contribute code back to YUI and other frameworks.

在一个拥有大量框架和库的生态系统中，YUI是一个专业且可扩展的典范。 我通过比较我和他们的代码和文档，以此来进一步地提高我的代码质量。尽管在这里我创建了一个框架作为例子，但是OOCSS实际上并不是一个框架，而是一种可伸缩的，理性的，可维护的CSS的方法。 也许最好的比喻是一种新的语言。 最终，它是一种不可定型的JavaScript库，并且我希望将代码贡献给YUI和其他框架。

## 一个CSS的框架是不正确的！ 我们不应该从头开始编码一切吗？（A framework for CSS is overkill! Shouldn't we code everything from scratch?）

Do you rewrite the math class every time you need a random number generated? 

意思是每次当您需要生成一个随机数时您还重写math类么?

CSS is hard, [not because it is broken](http://www.stubbornella.org/content/2009/02/12/css-doesn’t-suck-you’re-just-doing-it-wrong/) , but because it is a legitimate technology requiring expertise to architect correctly. It would be foolish to reinvent the wheel for every site.

CSS很难，[不仅是因为它是分散的](http://www.stubbornella.org/content/2009/02/12/css-doesn’t-suck-you’re-just-doing-it-wrong/)，还因为它是一个规范的技术，需要专业知识才能正确的构建。 为每个站点重新定义类这种方法才是愚蠢的。

## 右边栏在源文件中的顺序位于的主列之前，这会影响可访问性吗？会影响搜索引擎优化么？（The right column comes before the main column in the source order, will this impact accessibility? SEO?）

Early sites I worked on had a more normal template structure with an uber class on the body that showed or hid left and right columns based on the template. Users of the custom CMS got really frustrated when they would build a page in a three column layout, realize it needed to be two columns and find they had to start from scratch because there were multiple templates / starting points. You probably noticed that main is a liquid column, it expands to take all the room left over after the left and right columns have been rendered.

我工作的早期网站曾有一个更正常的模板结构，是一个基于模板的在主体上显示或隐藏左右列的超级类。 当他们在三列布局中构建一个页面的情况下，需要将其构建成成为两列时，他们会非常的沮丧，因为有多个模板/起点，他们发现他们必须从头开始做。 这里您可能会注意到，main主体是一个流式布局的列，在左列和右列已经被渲染之后，它占据了剩下的所有空间。

I prefer tab order to match visual order (because it is weird if tab order varies from that), but I also want a single template. As often happens in web development, two important goals came into conflict, and I made a judgement call about how to resolve it. In this case tab order matches visual order for everything except the right column. In the current code, the only requirement to create a left or right column is to put it in the HTML, no costly changes to make elsewhere in the dom.

我更喜欢tab的顺序来匹配视觉顺序（因为如果tab顺序与之不同的话，会让人感到很奇怪），但我也想要一个单一的模板。 正如web开发中经常遇到的那样，两个重要的目标发生冲突时，我就如何解决这个问题作出了判断。 在这种情况下，tab顺序序与除右列以外的所有内容相匹配。 在当前的代码中，唯一需要做的就是创建左边栏或者右边框，并将其放入HTML中，而不需要在DOM中的其他地方进行更改。

Screen reader users have two options: 

1. Skip links 
2. Navigation menus are always marked up as a list of links, or nested list of links. This is interesting because it allows screen reader users to skip the whole list via screen reader specific controls. 

屏幕阅读用户有两个选项：

1. 样式链接
2. 导航菜单始终标记为链接列表或嵌套的链接列表。 这很有趣，因为它允许屏幕阅读器用户通过屏幕阅读器的特定控件跳过整个列表。

Two ways to get past menus is sufficient IMO. 

得到过去的菜单的两个方法是充足的IMO。

Everyone seems to have an opinion re: SEO, and they are all different, and even opposed to one another.  :)  Given that climate, I'm inclined to think that, especially for navigation menus with a reasonable number of links, it just doesn't matter that much.  Once I did see the nav links being indexed in the content part of the search results, but that was years ago.  Search bots are pretty smart, I'm ready to assume that if I mark up my content in a semantic, clean way, and I'm not filling it out with a bunch of spam links, the bot should figure it out. 

每个人看起来似乎都有自己的意见：比如搜索引擎优化，他们都是基于不同的甚至相互反对的标准。 :)鉴于这种情况，我倾向于认为，特别是对于具有合理数量的链接的导航菜单，搜索引擎优化并不重要。 有一次，我看到了导航链接在搜索结果的内容部分中被编入索引，但那已经是几年前的事了。 搜索机制非常聪明，我更倾向于假设，如果我用一种语义，清晰的标记我的内容，而且我没有用一堆垃圾邮件链接来填充它，那么搜索机制应该能算出它。

Markup navigation menus as lists, which will allow screen reader users to skip them, and provide "skip to content" links. This provides a double fallback for accessibility. 

将列表导航菜单标记为列表，这将允许屏幕阅读用户跳过它们，并为他们提供“跳至内容”的链接。 这为可访问性提供了双重保障。

## 您已经使用了-hack了，为什么？ 我可以把这个代码放在一个单独的文件中吗？ 或者添加和IE特定的类？（You have used the _ hack, why? Can I put this code in a separate file? Or add and IE specific class?）

Obviously, the first consideration is keeping hacks as few and far between as possible.

1. Adding a separate stylesheet would add an additional HTTP request and increase total file size for a browser that already struggles with performance.
2. I like to keep all the code for any one object in one place. I think it helps minimize the number of hacks used especially as a project evolves over time.
3. Dev tools for IE6 and earlier are extremely primitive, which makes having hacks and normal code side by side even more important. I want to be able to figure out quickly when I have an IE bug which properties are coming into play. Again, I think this helps minimize hacks.
4. The spec indicates that properties which are not understood should be ignored by the browser. Given that the _ behavior of IE6 and earlier is very well known, I can reasonably expect that good browsers will always ignore this property.
5. Using conditional comments means that each html page has to contain a link to the IE specific stylesheet. One day (I can’t wait!) when IE6 market share drops to the minimal levels of IE5, I will turn off this code, but the last thing I want to do is touch 100s or 1000s of HTML pages. I’d rather have only CSS dependence on CSS hacks, rather than pushing this into the HTML. Unfortunately, IMHO the end of IE6 compatibility is farther off than we would like because quirksmode behavior in IE often falls back to an IE5.5 type model.

显而易见，首先要考虑的是尽可能减少hack。

1. 添加一个单独的样式表会增加一个额外的HTTP请求，并增加已经在性能方面有一定困难的浏览器中总文件的大小。
2. 我喜欢将任何一个对象的所有代码放在一个地方。我认为这有助于最大限度地减少使用hack的数量，特别是随着项目不断发展时这种现象更显著。
3. IE6及更早版本的开发工具是非常原始的，这使得hack和普通代码一起使用更为重要。当我遇到一个属性上出现的IE错误时，我希望能够快速找到答案。再次，我认为这有助于减少hack。
4. 规范指出浏览器应该忽略不理解的属性。鉴于IE6及更早版本的表现行为是众所周知的，我认为可以合理地预期，好的浏览器将永远忽略这些属性。
5. 使用条件注释意味着每个html页面都必须包含指向IE特定样式表的链接。有一天（我都等不及了！）当IE6的市场份额下降到IE5一样的最低水平，我会去掉这个代码，但我需要操作的是是100页或1000页的HTML页面。所以我宁愿CSS只依赖于CSShack，而不是把它推到HTML。不幸的是，恕我直言，IE6兼容性的结束比我们想要的更远，因为IE中的quirksmode行为往往会回落到IE5.5类型的模式。

I think my choice helps minimize the total number of hacks, improves performance, and has little future risk. On the other hand, if seeing the _ in your code makes you feel nauseous, you can absolutely move that to a separate file.

我认为我的选择有助于最大限度地减少hack总数并可以提高性能，而且这样做几乎没有任何风险。 另一方面，如果您在您的代码中看到会让您觉得不舒服，那么您可以把它移到一个单独的文件中。

## 容器对象使用空的`<b>`标签来添加边框等的表现效果，这对屏幕阅读用户来说不是问题吗？（The container objects use empty `<b>` tags to add presentational effects such as borders, won't this be a problem for screen reader users?）

Nope, luckily screen readers ignore empty b tags. I take advantage of this presentational fluff tag (b means bold) to apply presentational fluff. This markup should be included via a server-side script so that the day full css borders and drop shadows are supported we can turn off the script and have nice, clean, semantic html.

不会的,幸运的是，屏幕阅读器忽略b标签。 我利用这个表示性标签的优点（b表示粗体）来表示加粗。 这个标记应该存在于服务器端脚本中，这样就可以支持全部CSS边框和阴影，我们可以关闭脚本，并且有很好的清晰的语义化的html。

## 面向对象的CSS的方法采用了避免依赖于位置的风格。 这是否意味着我不应该使用像.myModule .title这样的后代选择器？（The OOCSS approach says avoid location-dependent styles. Does that mean I shouldn't use descendent selectors like .myModule .title?）

No--descendant selectors are not discouraged, but putting them too high in the DOM tree is. Avoid putting a wide-net class or id way up on the body or outermost divs of a page, and then writing lots of styles to generate variants of objects. It's not reusable, and it slows down page rendering. Instead, make a more "local" variant by adding a class directly onto the object (and add descendent styles to its children).

不是的，后代选择器不是不鼓励使用，但是它们在DOM树的位置过高了。 为了避免在网页的正文或最外面的div上放置wide-net类或id方式而编写大量样式来生成对象的超类。 这是不可重用的，它会减慢页面渲染速度。 相反的，我们应当通过在对象上直接添加一个类来创建一个更“本地”的超类（并将后代样式添加到其子元素中）。

A good rule of thumb is that anything within the body of a container is clearly a separate object.

一个好的方法是将容器内的任何东西看成是一个单独的对象。

This is questionable because the UL is clearly a separate object:

这的确令人疑惑，因为UL显然是一个单独的对象：

```css
#sidebar ul { ... }
```

so is this, because a carousel is clearly not part of the body object: 

这是因为滚动栏显然不是主体对象的一部分：

```css
body.browseProducts .carousel 
```

This is appropriate use of the cascade because the sub-node is really part of the larger parent object. b (corners) and inner clearly belong to the module, they can't exist on their own.:

这是级联的适当用法，因为子节点实际上是较大的父对象的一部分。 b（corners）和inner显然然属于模块，它们不能独立存在：

```css
.myModule { ... }
.myModule b { ... }
.myModule .inner { ... }
```

## 什么是叶子节点？（What is a Leaf Node?）

A leaf node is an element that doesn't contain other elements, e.g. `<strong>` or sometimes `<p>`， not sidebar or `<article>`.

一个叶子节点是一个不能包含其他元素的元素，例如`<strong>` 或者 `<p>`在某些时候的用法，而不是侧边栏或者`<article>`

## 您是不是应该有一个用面向对象的CSS构建的网站呢？（Do you have an example of a website built with OOCSS?）

There is a in-depth code review of a website made with OOCSS in the OOCSS Google Group. The link to the demo has moved to [http://waltschmidt.com/v2](http://waltschmidt.com/v2).You can also [read the full thread](http://groups.google.com/group/object-oriented-css/browse_thread/thread/be6cab782afa2fcf)(including the code review). Thanks to Walt for his permission to use his "first stab" as an example.

在谷歌OOCSS Group中，面向对象的CSS对网站进行了深入的代码审查。 演示的链接已移至[http://waltschmidt.com/v2](http://waltschmidt.com/v2)。您还可以[阅读完整的主题](http://groups.google.com/group/object-oriented-css/browse_thread/thread/be6cab782afa2fcf)（包括代码审查）。 此处感谢Walt允许以他的“first stab”为例。

## 我能帮助些什么？（How can I help?）

The best way to get involved is to start using the code (libraries, grids, fonts) and [submit bug reports and feature requests](http://stubbornella.lighthouseapp.com/projects/26663-object-oriented-css/tickets).  I also started a [OOCSS google group](http://groups.google.com/group/object-oriented-css) to facilitate discussion that is more complex than 140 twitter chars allows.

参与的最佳方式是开始使用这些代码（库，网格，字体）并[提交错误报告和功能请求](http://stubbornella.lighthouseapp.com/projects/26663-object-oriented-css/tickets)。 我还开办了一个[面向对象的CSS的谷歌小组](http://groups.google.com/group/object-oriented-css)，以此允许更加复杂的讨论。

