# 模板（Template）

[原文](https://github.com/stubbornella/oocss/wiki/Template)

Templates are used to solve common design patterns for page layout. Using these templates you can build pages which have a header, footer, left and right columns, and a main content area. Any of the sections can be broken up via [grids](https://github.com/stubbornella/oocss/wiki/grids). You can also use grids instead of columns. The main column is fully liquid, taking up all the rest of the space when the left column and right column have been rendered.

模板是用来解决页面布局的通用设计模式。使用这些模板，您可以构建一个拥有页眉、页脚、左右边栏和主体内容区域的页面。以上提到的任何部分都可以通过[网格](https://github.com/stubbornella/oocss/wiki/grids)来打破布局。您也可以使用网格来代替竖栏布局。主体栏是流式布局，当左右边栏已经被渲染后，主题栏会充满剩下的全部空间。

Please help me test the grids and template objects. Put them through their paces and let me know if you manage to break them!

请帮我测试网格和模板对象。请您测试它们的效果，如果您设法去打破布局，请您联系我！

## 基础类（Base Classes）

| Property | Description |
| --------- |---------|
| `page` | Main wraps site content. It can be extended via the classes `oldSchool` and `liquid` to provide 750px and full width layouts respectively. |
| `head` | Site header, generally contains custom code. (e.g. horizontal navigation, logo, search box) |
| `body` | Main content area, body of the page. |
| `foot` | Site footer, generally contains custom code. |
| `main` | Creates a main content area, often the center column. Fully liquid, it takes all remaining space when left and right columns have been rendered.  You may have 1 main columns. |
| `leftCol` | Creates a left column, default width is 250px. Extended by `gMail`, `gCal`, `yahoo`, and `myYahoo` to create widths of 160px, 180px, 240px, and 300px respectively. You may have 0-n left columns. |
| `rightCol` | Creates a right column, default width is 250px. Extended by `gMail`, `gCal`, `yahoo`, and `myYahoo` to create widths of 160px, 180px, 240px, and 300px respectively. You may have 0-n right columns. |
| `gMail` | Extends `leftCol` and `rightCol` to create a 160px column width. |
| `gCal` | Extends `leftCol` and `rightCol` to create a 180px column width. |
| `yahoo` | Extends `leftCol` and `rightCol` to create a 240px column width. |
| `myYahoo` | Extends `leftCol` and `rightCol` to create a 300px column width. |
| `oldSchool` | Extends `page` to create a 750px layout. |
| `liquid` | Extends `page` to create a full-width liquid layout. |


| 属性 | 描述 |
| --------- |---------|
| `页面（page）` | 网站内容的主体覆盖部分。它可以由`oldSchool`和`liquid`属性分别扩展为750px和全宽的布局。 |
| `页眉（head）` | 网站的页头，通常包括自定义代码组成。（比如由水平导航栏，logo，搜索框）|
| `主体（body）` | 主要的内容区域，是页面的主体部分。 |
| `页尾（foot）` | 网页的尾部，包括自定义代码部分。 |
| `主要区域（main）` | 构成了页面的主要内容区域，经常是中心栏。它全部是流式布局，会填充左右边栏渲染剩下的全部区域。您可以有一个主要的中心栏。 |
| `左边栏（leftCol）` | 构成了左边栏，默认的宽度是250px。可以分别由`gMail`, `gCal`, `yahoo` 和 `myYahoo` 属性扩展为160px, 180px, 240px, 和 300px。您可以有0个到n个左边栏。 |
| `右边栏（rightCol）` | 构成了右边栏，默认的宽度是250px。可以分别由`gMail`, `gCal`, `yahoo` 和 `myYahoo` 属性扩展为160px, 180px, 240px, 和 300px。您可以有0个到n个右边栏。 |
| `gMail` | 可以扩展`leftCol` 和 `rightCol`形成一个160px的列宽。 |
| `gCal` | 可以扩展`leftCol` 和 `rightCol`形成一个180px的列宽。 |
| `yahoo` | 可以扩展`leftCol` 和 `rightCol`形成一个240px的列宽。 |
| `myYahoo` | 可以扩展`leftCol` 和 `rightCol`形成一个300px的列宽。 |
| `oldSchool` | 可以扩展`page`形成一个750px宽的布局。 |
| `liquid` | 可以扩展`leftCol`形成一个全宽的流式布局。 |


## 基本模板（Basic template）
```
<div class="page">
	<div class="head"><!-- Head --></div>
	<div class="body"><!-- Body -->
		<div class="leftCol"><!-- Left Column (optional region) --></div>
		<div class="rightCol"><!-- Right Column (optional region) --></div>
		<div class="main"><!-- Main Content --></div>
	</div>
	<div class="foot"><!-- Foot --></div>	
</div>
```

##全宽模板，两列，gmail格式类型（Full width template, 2 columns, gmail style （160px left column width））
```
<div class="page liquid">
	<div class="head"><!-- Head --></div>
	<div class="body"><!-- Body -->
		<div class="leftCol gMail"><!-- Left Column (optional region) --></div>
		<div class="main"><!-- Main Content --></div>
		<!-- note: right column has been removed -->
	</div>
	<div class="foot"><!-- Foot --></div>	
</div>
```

## 目标（Goals）

In object oriented CSS the most important goal is to have a single template from which all pages are built.  This eases CMS development because by having a single starting point all pages can be made into any other page. Users of the CMS do not have traps in which a page they have built cannot be morphed into a different page type.  Another goal of an OO template is to have each section (column, header, etc) control its own destiny.  Practically, that means that if you want to add a left column to the template, the only required action should be actually adding the column to the HTML.  You never want to write CSS in such a way that changes are required higher in the DOM tree in order to make child elements behave properly.  Looping through the DOM is costly for CMS development. Similarly, if you want to have a different left column width, it should be accomplished by extending the left column object by adding an additional class. 

在面向对象的CSS中，最重要的目标就是可以为所有的页面创建一个单一通用的模板。这会缓轻CMS发展的压力，因为您可以从一个单页模板出发，构建成任何其他您所需要的页面。CMS用户也不必陷入一个单一页面没法变成不同页面类型的苦恼。另外一个面向对象的模板的目标就是每个部分（比如列，页头，等等）可以控制其本身的属性。特别的是，如果您想向模板中添加一列左边栏，您唯一要做的就是向HTML中添加一列竖列。您永远都不会希望通过编写CSS这种更加复杂的方式向DOM树种添加子元素来使得表现和添加HTML一致。循环整个DOM结构对于CMS的开发是很费事的。相似的，如果您想拥有一个不一样的列宽，唯一需要实现的就是为左边列对象添加一个额外的类。

### 扩展一个对象（Extending an object）

```
<div class="leftCol gMail"> ... </div>
```

## 制定模板（Customizing the template）

You may not find the default and extended widths of columns or pages match your site. In this case you can extend the column or main objects to allow custom widths. For performance reasons, you should avoid customizing templates whenever possible.

您也许找不到页面默认和扩展的列的宽度在哪里设置。这种情况下您可以通过自定义宽度来扩展列或者主体内容。但是出于表现性的原因，您应当尽量避免自定义模板。

### 列（Columns）

`myColumn` extends column objects to allow for custom column widths.

`myColum`通过扩展列对象以此来允许您自定义列的宽度。

```
.myColumn{width:400px;} 
```

### 主页（Main page）

`myPage`  extends `main`.

`myPage`扩展`main`。

```
.myPage{width:1050px !important;}
```

## 已知的问题（Known Issues）
- Source order - the right column is before the main content in the source order. This choice was made in order to allow the columns to be completely independent objects and to have one unique template rather than multiple starting points for a site. This speeds and simplifies CMS development and enhances usability for those creating pages within the CMS. Skip to content links and navigational items marked up as lists are strongly encouraged.

- 源文件顺序 - 在源文件中，右边栏的顺序应当先于主体内容的部分。这个决定是为了使得边栏可以成为完全独立的对象，并且对于整个网站，有唯一的模板而不是可以从多个起点开始编码。这个决定可以加速和简化CMS的开发并且提高使用CMS编写的页面的稳定性。并且我们强烈推荐跳过内容链接并使用将导航项目标记成清单的形式。

- Overflow - the containing blocks are made to wrap floats using the contexte de formattage; `overflow:hidden; _overflow:visible; zoom:1;`. This is known to cause printing bugs in older versions of Firefox and can cause absolutely positioned blocks originating in that container to be cropped. Removing floats and overflow via the print stylesheet is a corrective option.

- 溢出 - 包含块使用内容格式化的方式包含浮动块；`overflow:hidden; _overflow:visible; zoom:1;`。在老版本的Firefox中这会造成打印bug并将包含在该该块的绝对定位的块级元素被截短。针对这种情况，通过样式表移除浮动和溢出是一个不错的选择。
