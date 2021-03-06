title: 01、面向对象的CSS（Object Oriented CSS）
categories: [理论, css, oocss]
date: 2018/01/02 09:30:00
tags: [理论, css, oocss]
---


[原文](https://github.com/stubbornella/oocss/wiki)

<div style="position: relative; box-sizing: border-box; width: 100%; max-width: 100%; height: 0; padding-top: 81.00%; border:1px solid #ccc;"><iframe src="//www.slideshare.net/slideshow/embed_code/key/EUTjDAdG7npnxS" width="100%" height="100%" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;" allowfullscreen> </iframe></div>


How do you scale CSS for thousands of pages? Object Oriented CSS is an answer. It's an approach for writing CSS that's fast, maintainable, and standards-based. It adds much needed predictability to CSS so that even beginners can participate in writing beautiful websites. Nicole Sullivan first presented it at Web Directions North in Denver and the response has been overwhelming.

如何在大量的页面中重用CSS呢？面向对象的CSS是一个不错的选择。这是一种快速编写可维护、标准化CSS代码的方法。为CSS添加了急需的可预测性，即使初学者也能参与编写完美的网站。尼科尔·沙利文（Nicole Sullivan）在丹佛的“Web Directions North”会议上首次提出，获得了很大反响。

This Github project is for the OOCSS framework—a collection of code that's built using the OOCSS approach and is meant to help you get started. However, the framework is not the same thing as the OOCSS idea. (Confusingly though, they have the same name...that'll probably change.)

这个[Github项目](https://github.com/stubbornella/oocss)就是一个OOCSS框架——使用OOCSS方法构建起来的代码集合，旨在帮助您起步使用。但是，这个框架和OOCSS的思想是两码事（它们只是名字相同而已...以后也许会改变一下）。


### 什么是CSS对象？（What's a CSS Object?）

Basically, a CSS "object" is a repeating visual pattern, that can be abstracted into an independent snippet of HTML, CSS, and possibly JavaScript. That object can then be reused throughout a site. 

根本上说，CSS “对象”是一种可复用的可视化模式，可以被抽象为独立的HTML，CSS和必要的JavaScript片段。然后可以在整站中重用该对象。

For instance, in the OOCSS framework the [media object](https://github.com/stubbornella/oocss/wiki/Content#template) describes a content block containing a fixed-size media element (e.g. image or video) along with other variable-size content (e.g. text). Another example is the [module object](https://github.com/stubbornella/oocss/wiki/Module), which describes a generic content block with a required body area and optional header and footer areas. 

例如，在OOCSS框架中，[媒体对象](https://github.com/stubbornella/oocss/wiki/Content#template)用来表示内容容器，包含固定大小的媒体元素（例如图像或视频）和其他可变大小的内容（例如文本）。另一个例子是[模块对象](https://github.com/stubbornella/oocss/wiki/Module)，它用来表示通用的内容块，包含必需的主体部分和可选的页眉、页尾区域。

[想要了解更多有关对象的内容，请参见FAQ页面...](https://github.com/stubbornella/oocss/wiki/FAQ)


### OOCSS的两个主要原则（Two Main Principles of OOCSS）
 - 分离结构和外观（Separate structure and skin ）

This means to define repeating visual features (like background and border styles) as separate "skins" that you can mix-and-match with your various objects to achieve a large amount of visual variety without much code. See the [module object](/standard/2018/06/26/05、模块-容器对象（modules-container-objects）.html) and [its skins](/standard/2018/06/26/06、模块皮肤（module-skins）.html).

这意味着需要将重复的视觉特征（如背景和边框样式）定义为单独的“皮肤”，与各种对象进行混合和匹配，用少量的代码得到广泛的使用。请参阅[模块对象](/standard/2018/06/26/05、模块-容器对象（modules-container-objects）.html)和[模块皮肤](/standard/2018/06/26/06、模块皮肤（module-skins）.html)。

Separating structure and skin can also mean using classes to name your objects and their components, rather than relying solely on the semantics of HTML. For example, the media object is named with `class="media"`, and its components are named with `class="img"` (for the image/video component) and `class="bd"` (for the body/text component).

分离结构和外观意味着使用类命名对象及其组件，而不是仅依赖于HTML的语义。例如，媒体对象以 `class="media"` 命名，其组件以`class="img"`（对于图像/视频组件）和`class="bd"`（用于主体body/文本组件）命名。

By referencing these classes in your stylesheets (say, rather than directly styling the `<img>` element), your HTML can be flexible. For instance, if a new media element were to take off in the next few years (e.g. `<svg>`), it could be integrated into the HTML without having to touch the CSS.

通过在样式表中引用这些类（比如说，相对于直接使用`<img>`元素这样的样式），你的HTML将会更加灵活。例如，如果一个新的媒体元素在未来几年内将会大量使用（比如`<svg>`），通过这种方式，您可以在不接触CSS的情况下将它融入到HTML中。

- 分离容器和内容（Separate container and content）

Essentially, this means “rarely use location-dependent styles”. An object should look the same no matter where you put it. So instead of styling a specific `<h2>` with `.myObject h2 {...}`, create and apply a class that describes the `<h2>` in question, like `<h2 class="category">`.

本质上，这意味着“杜绝使用位置依赖的样式风格”。无论将一个元素放在哪里，对象的表现形式都应该是一样的。所以，不同于对`<h2>`添加诸如`.myObject h2 {...}`这样的特殊样式，应该用同一个类诸如`<h2 class="category">`来描述`<h2>`。

This gives you the assurance that: (1) all unclassed `<h2>`s will look the same; (2) all elements with the category class (called a mixin) will look the same; and 3) you won't need to create an override style for the case when you actually do want `.myObject h2` to look like the normal `<h2>`.</p>

这样就可以向您保证：（1）所有没有类属性的`<h2>`看起来都一样；（2）所有具有某个类别类的元素（称为mixin）看起来都一样；（3）当需要`.myObject h2`和普通的`<h2>`看起来一样时，不需要再创建一个覆盖样式。

## 入门（Getting Started）
[//]: # (这部分翻译的很好，不用改)
1. Download all the files and set up a local directory.
2. Open template.html (this is the basic template you will modify to create all other pages).
3. Set your left and right column widths by [extending the column objects](https://github.com/stubbornella/oocss/wiki/faq#extend)
4. Use grids to break the page up further into smaller sections.
5. Test site functionality by adding content objects from the content.css file. (These can also be found in library.html).


1. 下载所有文件并设置本地目录。
2. 打开template.html（这是您将修改创建所有其他页面的基本模板）。
3. 通过[扩展列对象](https://github.com/stubbornella/oocss/wiki/faq#extend)来设置左右列宽。
4. 使用网格将页面进一步分割成较小的部分。
5. 通过从content.css文件添加内容对象来测试站点功能。（这些也可以在library.html中找到）。

## 准备进行Alpha测试（Ready for alpha testing）
Please help me test the talk bubble objects! Put them through their paces and let me know if you manage to break them. Add feature requests under the "issues" tab.


请帮我测试谈话泡泡对象！通过观察他们，当如果您试图去刺破它，请让我知道。在“问题”选项卡下添加功能请求。

- Tabs (very experimental)
- Talk Bubbles
- Content Objects (particularly media)


- 标签（很有实践用处）
- 谈话泡
- 内容对象（尤其是媒体对象）

## 稳定性（Stable）
- Module
- Template
- Grids


- 模块
- 模板
- 网格

## 基础库（Base Libraries）
OOCSS is built on top of reset and fonts from the YUI libraries.  These libraries provide a common starting point across different navigators.

OOCSS的基础是建立在YUI库的重置库（reset）和字体（font）之上的。这些库磨平了浏览器之间的差异，提供了一个同样的起点。

- Reset and Fonts from YUI are a starting point.

- 以YUI中重置库（Reset）和字体库（Fonts）为起点。

## 未来（Upcoming）
- Content objects
- DHTML blocks (tabs, carousel, toggle, etc)

- 内容对象
- DHTML块（标签，轮播，切换等）

## 感谢！（Thanks!）
I've had the good fortune to work/study/play with some amazing developers, engineers, managers, designers, and visionaries over the years.  All of them contributed in different ways to shaping my ideas about how CSS should be built and maintained.  

多年来，我一直有幸与一些杰出的开发人员，工程师，项目管理人员，设计师和一些有远见的人一起工作/学习/娱乐。他们都在以不同的方式帮助我实现更好的构建和维护CSS的理想。

Many many thanks to Arnaud Gueras, Florian Harmel,  Sebastian Tiphaine, Yann Doussot, Thomas Vial, Adrien Thery, Sebastien Cardif, Thomas Vergnaud, Etienne Bernard, Yannick Bonnieux, Renaud Boyerand, Matt Sweeney, Nate Koechley, Leslie Jensen-Inman, Philip Tellis, Stoyan Stefanov, Robin Garner, Kevin Michel, Christophe Dubois, Orphelie Dudemaine, Medhi El Azmi, Christophe Charles, Eric Prudhommeaux, Mark Mason, Tenni Theurer, Steve Souders, Jennifer Le Hegaret, Praveen P N, Doug Crockford, Nicholas Zakas, Mark Norman Francis, Christian Heilmann, Jenny Han Donnelly, Tom Croucher, Brian Rountree, Ryan Grove, Philippe Mihelic, Stephanie Troeth, Nick Fogler, Gonzalo Cordero and the other Jukus, and Dan Cederholm and his book bulletproof. 

十分感谢以下所有人员：Arnaud Gueras, Florian Harmel, Sebastian Tiphaine, Yann Doussot, Thomas Vial, Adrien Thery, Sebastien Cardif, Thomas Vergnaud, Etienne Bernard, Yannick Bonnieux, Renaud Boyerand, Matt Sweeney, Nate Koechley, Leslie Jensen-Inman, Philip Tellis, Stoyan Stefanov, Robin Garner, Kevin Michel, Christophe Dubois, Orphelie Dudemaine, Medhi El Azmi, Christophe Charles, Eric Prudhommeaux, Mark Mason, Tenni Theurer, Steve Souders, Jennifer Le Hegaret, Praveen P N, Doug Crockford, Nicholas Zakas, Mark Norman Francis, Christian Heilmann, Jenny Han Donnelly, Tom Croucher, Brian Rountree, Ryan Grove, Philippe Mihelic, Stephanie Troeth, Nick Fogler, Gonzalo Cordero and the other Jukus, and Dan Cederholm和他的防弹书。

I'm sure I've forgotten some... deepest apologies.

我很确定我遗忘了一些人....对此感到深深地抱歉。

> “If you can't be a good example, then you'll just have to serve as a horrible warning.” 
> —— Catherine Aird

> “如果你不能成为一个好榜样，那么你只能作为一个可怕的警告。”
> —— 凯瑟琳艾尔德
