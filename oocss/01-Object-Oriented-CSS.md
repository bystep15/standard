# 面向对象的CSS（Object Oriented CSS）

[原文](https://github.com/stubbornella/oocss/wiki)

<iframe src="//www.slideshare.net/slideshow/embed_code/key/EUTjDAdG7npnxS" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe>

<> (This is a comment, it will not be included)
<上部分是原翻译，下部分是我翻译的，只有一段翻译的是原翻译不全>
如何在数千页面上重用CSS？面向对象的CSS是一个答案。它是开发编写快速，可维护和基于标准的CSS一种方法。它为CSS增加了非常需要的可预测性，以便即使是初学者也可以参与编写漂亮的网站。尼科尔·沙利文（Nicole Sullivan）首先在丹佛的“Web Directions North”上提出，之后反响非常好。
你会如何在数千页面上重用CSS？面向对象的CSS是一个不错的选择。它是一种可以编写快速、可维护并基于标准的CSS的方法。它为CSS增加了其非常需要的可预测性，以便即使是初学者也能参与编写完美的网站。它是由尼科尔·沙利文（Nicole Sullivan）在丹佛的“Web Directions North”会议上第一次提出的，并且获得了非常好的反响。
How do you scale CSS for thousands of pages? Object Oriented CSS is an answer. It's an approach for writing CSS that's fast, maintainable, and standards-based. It adds much needed predictability to CSS so that even beginners can participate in writing beautiful websites. Nicole Sullivan first presented it at Web Directions North in Denver and the response has been overwhelming.

这个Github项目就是一个OOCSS框架，使用OOCSS方法构建的代码集合，旨在帮助您开始使用。但是，这个框架和OOCSS的思想并不是一回事。（这很领人困惑，他们有相同的名字，这可能会改变。）
这个GitHub项目就是基于面向对象的CSS（OOCSS）框架编写的，OOCSS框架是一种由OOCSS方法构建的代码集合，并旨在帮助您更好的使用OOCSS。但是，这个框架和OOCSS思想并不是一回事。（它们有相同的名称的确让人感到困扰...以后也许会有所改变吧。）
This Github project is for the OOCSS framework—a collection of code that's built using the OOCSS approach and is meant to help you get started. However, the framework is not the same thing as the OOCSS idea. (Confusingly though, they have the same name...that'll probably change.)

###什么是CSS对象？（What's a CSS Object?）

基本上，CSS “对象”是一种重复的可视化模式，可以被抽象为独立的HTML，CSS和必要的JavaScript片段。然后可以在整个站点中重用该对象。
简而言之，CSS“对象”是一种可以重复使用的可视化模式，它可以从HTML，CSS和必要的JavaScript中抽象为独立的片段。抽象出的对象可以被整个网站重用。
Basically, a CSS "object" is a repeating visual pattern, that can be abstracted into an independent snippet of HTML, CSS, and possibly JavaScript. That object can then be reused throughout a site. 

例如，在OOCSS框架中，[媒体对象](https://github.com/stubbornella/oocss/wiki/Content#template)描述包含固定大小的媒体元素（例如图像或视频）以及其他可变大小的内容（例如文本）的内容块。另一个例子是[模块对象](https://github.com/stubbornella/oocss/wiki/Module)，它描述具有所需体区和可选的页眉和页脚区域的通用内容块。
例如，在OOCSS框架中，[媒体对象](https://github.com/stubbornella/oocss/wiki/Content#template)是一种描述包含固定大小的媒体元素（例如图像或视频）与可变大小的内容（例如文本）的内容块。另一个例子是[模块对象](https://github.com/stubbornella/oocss/wiki/Module)，它是一种具有必要的主体部分和可选的页眉和页尾区域的通用内容块。
For instance, in the OOCSS framework the [media object](https://github.com/stubbornella/oocss/wiki/Content#template) describes a content block containing a fixed-size media element (e.g. image or video) along with other variable-size content (e.g. text). Another example is the [module object](https://github.com/stubbornella/oocss/wiki/Module), which describes a generic content block with a required body area and optional header and footer areas. 

详细了解这些对象，请参看FAQ页面...
想要了解更多有关对象的内容，请参见FAQ页面...
[Read more about objects on the FAQ page…](https://github.com/stubbornella/oocss/wiki/FAQ)

###OOCSS的两个主要原则（Two Main Principles of OOCSS）
 - 分离结构性内容和语义化内容（Separate structure and skin ）

这意味着将重复的视觉特征（如背景和边框样式）定义为单独的“皮肤”，您可以将其与各种对象进行混合和匹配，以获得大量的视觉品种而无需多少代码。请参阅[模块对象](https://github.com/stubbornella/oocss/wiki/Module)和[其皮肤](https://github.com/stubbornella/oocss/wiki/Module-Skins)。
这意味着将重复的可视化特性（如背景和边框样式）定义为独立的语义化内容（皮肤），您可以将其与您不同的对象混合并匹配，以获得无需多少代码就能实现大量不同的视觉特性。详情请参阅[模块对象](https://github.com/stubbornella/oocss/wiki/Module)和[其皮肤](https://github.com/stubbornella/oocss/wiki/Module-Skins)。
 This means to define repeating visual features (like background and border styles) as separate "skins" that you can mix-and-match with your various objects to achieve a large amount of visual variety without much code. See the [module object](https://github.com/stubbornella/oocss/wiki/Module) and [its skins](https://github.com/stubbornella/oocss/wiki/Module-Skins).

分离结构和皮肤也可以意味着使用类命名对象及其组件，而不是仅依赖于HTML的语义。例如，媒体对象以 `class="media"` 命名，其组件以`class="img"`（对于图像/视频组件）和`class="bd"`（用于主体body/文本组件）命名。
分离结构性与语义性也意味着您可以使用类的命名格式来命名您的对象和它们的组件，而不是仅仅依赖于HTML的语义。例如，媒体对象可以命名为`class="media"`，它的组件可以命名为`class="img"`（对于图像和视频组件）和`class="bd"`（对于主体和文本组件）。
 Separating structure and skin can also mean using classes to name your objects and their components, rather than relying solely on the semantics of HTML. For example, the media object is named with `class="media"`, and its components are named with `class="img"` (for the image/video component) and `class="bd"` (for the body/text component).

通过在样式表中引用这些类（比如说，相对于直接使用`<img>`元素这样的样式），你的HTML将会更加灵活。例如，如果一个新的媒体元素在未来几年内将会大量使用（比如`<svg>`），通过这种方式，您可以在不接触CSS的情况下将它融入到HTML中。
 By referencing these classes in your stylesheets (say, rather than directly styling the `<img>` element), your HTML can be flexible. For instance, if a new media element were to take off in the next few years (e.g. `<svg>`), it could be integrated into the HTML without having to touch the CSS.

- 分离容器和内容（Separate container and content）

 本质上，这意味着“很少使用与位置有关的风格”。无论你放在哪里，对象都应该是一样的。因此，而不是样式化特定`<h2>` `.myObject h2 {...}`，创建和应用描述一类`<h2>`的问题，如`<h2 class="category">`
 从本质上来说，这意味着“位置与样式无关”。无论您将一个元素放在那里，它的表现形式都应该是一样的。所以，不同于对`<h2>`添加诸如`.myObject h2 {...}`这样的特殊样式，应该用同一个类诸如`<h2 class="category">`来描述`<h2>`。
Essentially, this means “rarely use location-dependent styles”. An object should look the same no matter where you put it. So instead of styling a specific `<h2>` with `.myObject h2 {...}`, create and apply a class that describes the `<h2>` in question, like `<h2 class="category">`.

这样就可以保证：1）所有未分类`<h2>`的都将看起来一样; 2）具有类别类的所有元素（称为mixin）将看起来一样; 3）您不需要创建一个覆盖样式的情况下，当你真的想要`.myObject h2`看起来像正常`<h2>`。
这样就可以向您保证：（1）所有没有类属性的`<h2>`看起来都一样；（2）所有具有某个类别类的元素（称为mixin）看起来都一样；（3）当您想让`.myObject h2`看起来跟正常的`<h2>`一样时，您不必创建一个覆盖样式。
This gives you the assurance that: (1) all unclassed `<h2>`s will look the same; (2) all elements with the category class (called a mixin) will look the same; and 3) you won't need to create an override style for the case when you actually do want `.myObject h2` to look like the normal `<h2>`.</p>

##入门（Getting Started）
---------
<这部分翻译的很好，不用改>
1. 下载所有文件并设置本地目录。
2. 打开template.html（这是您将修改创建所有其他页面的基本模板）。
3. 通过[扩展列对象](https://github.com/stubbornella/oocss/wiki/faq#extend)来设置左右列宽。
4. 使用网格将页面进一步分割成较小的部分。
5. 通过从content.css文件添加内容对象来测试站点功能。（这些也可以在library.html中找到）。

1. Download all the files and set up a local directory.
2. Open template.html (this is the basic template you will modify to create all other pages).
3. Set your left and right column widths by[extending the column objects] (https://github.com/stubbornella/oocss/wiki/faq#extend)
4. Use grids to break the page up further into smaller sections.
5. Test site functionality by adding content objects from the content.css file. (These can also be found in **library.html**).

##准备进行Alpha测试（Ready for alpha testing）
---------
请帮我测试谈话泡泡对象！把他们穿过他们的步伐，让我知道如果你设法打破他们。在“问题”选项卡下添加功能请求。
请帮助我测试谈话泡对象！通过观察他们，当如果您试图去刺破它，请让我知道。在“问题”选项卡下添加功能请求。
Please help me test the talk bubble objects! Put them through their paces and let me know if you manage to break them. Add feature requests under the "issues" tab.

- 标签（很有实践用处）
- 谈话泡
- 内容对象（尤其是媒体对象）

-  Tabs (very experimental)
-  Talk Bubbles
-  Content Objects (particularly media)

##稳定性（Stable）
---------
- 模块
- 模板
- 网格

- Module
- Template
-  Grids

##基础库（Base Libraries）
---------
OOCSS是建立在YUI库的重置与字体上。这些库提供了不同浏览器的共同起点。
OOCSS的基础是建立在YUI库的重置库（reset）和字体（font）之上的。这些库为不同的浏览器提供了共同的起点。
OOCSS is built on top of reset and fonts from the YUI libraries.  These libraries provide a common starting point across different navigators.

- 来自YUI的重置和字体是一个起点。
- YUI中重置库（Reset）和字体库（Fonts）仅仅是一个起点。
- Reset and Fonts from YUI are a starting point.

##未来（Upcoming）
---------
- 内容对象
- DHTML块（标签，轮播，切换等）

- Content objects
- DHTML blocks (tabs, carousel, toggle, etc)

##感谢！（Thanks!）

多年来，我一直有幸与一些惊人的开发人员，工程师，经理，设计师和梦想家一起工作/学习/玩耍。所有这些都以不同的方式帮助了我如何构建和维护CSS的想法。
多年来，我一直有幸与一些杰出的开发人员，工程师，项目管理人员，设计师和一些有远见的人一起工作/学习/娱乐。他们都在以不同的方式帮助我实现更好的构建和维护CSS的理想。
I've had the good fortune to work/study/play with some amazing developers, engineers, managers, designers, and visionaries over the years.  All of them contributed in different ways to shaping my ideas about how CSS should be built and maintained.  

十分感谢以下所有人员：Arnaud Gueras, Florian Harmel, Sebastian Tiphaine, Yann Doussot, Thomas Vial, Adrien Thery, Sebastien Cardif, Thomas Vergnaud, Etienne Bernard, Yannick Bonnieux, Renaud Boyerand, Matt Sweeney, Nate Koechley, Leslie Jensen-Inman, Philip Tellis, Stoyan Stefanov, Robin Garner, Kevin Michel, Christophe Dubois, Orphelie Dudemaine, Medhi El Azmi, Christophe Charles, Eric Prudhommeaux, Mark Mason, Tenni Theurer, Steve Souders, Jennifer Le Hegaret, Praveen P N, Doug Crockford, Nicholas Zakas, Mark Norman Francis, Christian Heilmann, Jenny Han Donnelly, Tom Croucher, Brian Rountree, Ryan Grove, Philippe Mihelic, Stephanie Troeth, Nick Fogler, Gonzalo Cordero and the other Jukus, and Dan Cederholm和他的防弹书。
Many many thanks to Arnaud Gueras, Florian Harmel,  Sebastian Tiphaine, Yann Doussot, Thomas Vial, Adrien Thery, Sebastien Cardif, Thomas Vergnaud, Etienne Bernard, Yannick Bonnieux, Renaud Boyerand, Matt Sweeney, Nate Koechley, Leslie Jensen-Inman, Philip Tellis, Stoyan Stefanov, Robin Garner, Kevin Michel, Christophe Dubois, Orphelie Dudemaine, Medhi El Azmi, Christophe Charles, Eric Prudhommeaux, Mark Mason, Tenni Theurer, Steve Souders, Jennifer Le Hegaret, Praveen P N, Doug Crockford, Nicholas Zakas, Mark Norman Francis, Christian Heilmann, Jenny Han Donnelly, Tom Croucher, Brian Rountree, Ryan Grove, Philippe Mihelic, Stephanie Troeth, Nick Fogler, Gonzalo Cordero and the other Jukus, and Dan Cederholm and his book bulletproof. 

我很确定我遗忘了一些人....对此感到深深地抱歉。
I'm sure I've forgotten some... deepest apologies.

> 士不可以不弘毅，任重而道远。仁以为己任，不亦重乎？死而后已，不亦远乎？
> “若不能成为典范，那你只能作为警示以被世人警惕。”
> Catherine Aird

> “If you can't be a good example, then you'll just have to serve as a horrible warning.” 
> Catherine Aird


