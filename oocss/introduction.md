# Object Oriented CSS 面向对象的CSS

How do you scale CSS for thousands of pages? Object Oriented CSS is an answer. It’s an approach for writing CSS that’s fast, maintainable, and standards-based. It adds much needed predictability to CSS so that even beginners can participate in writing beautiful websites. Nicole Sullivan first presented it at Web Directions North in Denver and the response has been overwhelming.
如何在数千页面上重用CSS？面向对象的CSS是一个答案。它是开发编写快速，可维护和基于标准的CSS一种方法。它为CSS增加了非常需要的可预测性，以便即使是初学者也可以参与编写漂亮的网站。尼科尔·沙利文（Nicole Sullivan）首先在丹佛的“Web Directions North”上提出，之后反响非常好。

This Github project is for the OOCSS framework—a collection of code that’s built using the OOCSS approach and is meant to help you get started. However, the framework is not the same thing as the OOCSS idea. (Confusingly though, they have the same name…that’ll probably change.)
这个Github项目就是一个OOCSS框架，使用OOCSS方法构建的代码集合，旨在帮助您开始使用。但是，这个框架和OOCSS的思想并不是一回事。（这很领人困惑，他们有相同的名字，这可能会改变。）

### What’s a CSS Object? 什么是CSS对象？

Basically, a CSS “object” is a repeating visual pattern, that can be abstracted into an independent snippet of HTML, CSS, and possibly JavaScript. That object can then be reused throughout a site.
基本上，CSS “对象”是一种重复的可视化模式，可以被抽象为独立的HTML，CSS和必要的JavaScript片段。然后可以在整个站点中重用该对象。

For instance, in the OOCSS framework the media object describes a content block containing a fixed-size media element (e.g. image or video) along with other variable-size content (e.g. text). Another example is the module object, which describes a generic content block with a required body area and optional header and footer areas.
例如，在OOCSS框架中，媒体对象描述包含固定大小的媒体元素（例如图像或视频）以及其他可变大小的内容（例如文本）的内容块。另一个例子是模块对象，它描述具有所需体区和可选的页眉和页脚区域的通用内容块。

Read more about objects on the FAQ page…
详细了解这些对象，请参看FAQ页面

### Two Main Principles of OOCSS OOCSS的两个主要原则

#### Separate structure and skin 分离结构和皮肤

This means to define repeating visual features (like background and border styles) as separate “skins” that you can mix-and-match with your various objects to achieve a large amount of visual variety without much code. See the module object and its skins.
这意味着将重复的视觉特征（如背景和边框样式）定义为单独的“皮肤”，您可以将其与各种对象进行混合和匹配，以获得大量的视觉品种而无需多少代码。请参阅[模块对象]()和其[皮肤]()。

Separating structure and skin can also mean using classes to name your objects and their components, rather than relying solely on the semantics of HTML. For example, the media object is named with class="media", and its components are named with class="img" (for the image/video component) and class="bd" (for the body/text component).
分离结构和皮肤也可以意味着使用类命名对象及其组件，而不是仅依赖于HTML的语义。例如，媒体对象以 class="media" 命名，其组件以class="img"（对于图像/视频组件）和class="bd"（用于主体body/文本组件）命名。

By referencing these classes in your stylesheets (say, rather than directly styling the <img> element), your HTML can be flexible. For instance, if a new media element were to take off in the next few years (e.g. <svg>), it could be integrated into the HTML without having to touch the CSS.
通过在样式表中引用这些类（比如说，而不是直接样式化<img>元素），你的HTML可以是灵活的。例如，如果新的媒体元素在未来几年（例如<svg>）流行起来，则可以将其集成到HTML中，而不必修改CSS。

#### Separate container and content 分离容器和内容

Essentially, this means “rarely use location-dependent styles”. An object should look the same no matter where you put it. So instead of styling a specific `<h2>` with .myObject h2 {...}, create and apply a class that describes the `<h2>` in question, like `<h2 class="category">`.
本质上，这意味着“很少使用与位置有关的风格”。无论你放在哪里，对象都应该是一样的。因此，而不是样式化特定`<h2>` .myObject h2 {...}，创建和应用描述一类`<h2>`的问题，如`<h2 class="category">`。

This gives you the assurance that: (1) all unclassed <h2>s will look the same; (2) all elements with the category class (called a mixin) will look the same; and 3) you won’t need to create an override style for the case when you actually do want .myObject h2 to look like the normal `<h2>`.
这样就可以保证：1）所有未分类`<h2>`的都将看起来一样; 2）具有类别类的所有元素（称为mixin）将看起来一样; 3）您不需要创建一个覆盖样式的情况下，当你真的想要.myObject h2看起来像正常`<h2>`。

## Getting Started 入门

1. Download all the files and set up a local directory.
2. Open template.html (this is the basic template you will modify to create all other pages).
3. Set your left and right column widths by extending the column objects
4. Use grids to break the page up further into smaller sections.
5. Test site functionality by adding content objects from the content.css file. (These can also be found in library.html).

1. 下载所有文件并设置本地目录。
2. 打开template.html（这是您将修改创建所有其他页面的基本模板）。
3. 通过扩展列对象来设置左右列宽
4. 使用网格将页面进一步分割成较小的部分。
5. 通过从content.css文件添加内容对象来测试站点功能。（这些也可以在library.html中找到）。

## Ready for alpha testing 准备进行Alpha测试

*Please help me test the talk bubble objects! Put them through their paces and let me know if you manage to break them. Add feature requests under the “issues” tab.*
*请帮我测试谈话泡泡对象！把他们穿过他们的步伐，让我知道如果你设法打破他们。在“问题”选项卡下添加功能请求。*

* Tabs (very experimental)
* Talk Bubbles
* Content Objects (particularly media)

* 标签（非常实验）
* 说话泡泡
* 内容对象（特别是媒体）

## Stable 稳定

* Module
* Template
* Grids

* 模块
* 模板
* 网格

## Base Libraries 基础库

OOCSS is built on top of reset and fonts from the YUI libraries. These libraries provide a common starting point across different navigators.
OOCSS是建立在YUI库的*重置*与*字体*上。这些库提供了不同浏览器的共同起点。

* Reset and Fonts from YUI are a starting point. 
* 来自YUI的重置和字体是一个起点。

## Upcoming 即将到来

* Content objects
* DHTML blocks (tabs, carousel, toggle, etc)


* 内容对象
* DHTML块（标签，轮播，切换等）

## Thanks! 谢谢！

I’ve had the good fortune to work/study/play with some amazing developers, engineers, managers, designers, and visionaries over the years. All of them contributed in different ways to shaping my ideas about how CSS should be built and maintained.
多年来，我有幸与一些惊人的开发人员，工程师，经理，设计师和梦想家一起工作/学习/玩耍。所有这些都以不同的方式帮助了我如何构建和维护CSS的想法。

Many many thanks to Arnaud Gueras, Florian Harmel, Sebastian Tiphaine, Yann Doussot, Thomas Vial, Adrien Thery, Sebastien Cardif, Thomas Vergnaud, Etienne Bernard, Yannick Bonnieux, Renaud Boyerand, Matt Sweeney, Nate Koechley, Leslie Jensen-Inman, Philip Tellis, Stoyan Stefanov, Robin Garner, Kevin Michel, Christophe Dubois, Orphelie Dudemaine, Medhi El Azmi, Christophe Charles, Eric Prudhommeaux, Mark Mason, Tenni Theurer, Steve Souders, Jennifer Le Hegaret, Praveen P N, Doug Crockford, Nicholas Zakas, Mark Norman Francis, Christian Heilmann, Jenny Han Donnelly, Tom Croucher, Brian Rountree, Ryan Grove, Philippe Mihelic, Stephanie Troeth, Nick Fogler, Gonzalo Cordero and the other Jukus, and Dan Cederholm and his book bulletproof.
许多感谢Arnaud Gueras，Florian Harmel，Sebastian Tiphaine，Yann Doussot，Thomas Vial，Adrien Thery，Sebastien Cardif，Thomas Vergnaud，Etienne Bernard，Yannick Bonnieux，Renaud Boyerand，Matt Sweeney，Nate Koechley，Leslie Jensen-Inman，Philip Tellis ，斯托扬·斯特凡诺夫，罗宾·加纳，凯文·米歇尔，克里斯托弗·杜波伊斯，奥菲尔·杜德曼，艾迪·阿兹米，克里斯托夫·查尔斯，埃里克·普鲁多米奥，马克·梅森，蒂尼·理雷尔，史蒂夫·斯德尔斯，珍妮弗·勒·海格雷特，普拉文恩，道格·克罗克福德，尼古拉斯·扎卡斯，马克·诺曼Francis，Christian Heilmann，Jenny Han Donnelly，Tom Croucher，Brian Rountree，Ryan Grove，Philippe Mihelic，Stephanie Troeth，Nick Fogler，Gonzalo Cordero和其他Jukus，以及Dan Cederholm和他的防弹书。

I’m sure I’ve forgotten some… deepest apologies.
我相信我还是忘记了一些朋友...最深切的道歉。

> “If you can’t be a good example, then you’ll just have to serve as a horrible warning.” 
> Catherine Aird

> “如果你不能成为一个很好的例子，那么你只需要作为一个可怕的警告。”
> 凯瑟琳·阿里