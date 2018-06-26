title: 02、模板（Template）
categories: [理论, css, oocss]
date: 2018/05/29 09:30:00
tags: [理论, css, oocss]
---


[原文](https://github.com/stubbornella/oocss/wiki/Template)

Templates are used to solve common design patterns for page layout. Using these templates you can build pages which have a header, footer, left and right columns, and a main content area. Any of the sections can be broken up via [grids](https://github.com/bystep15/standard/blob/master/oocss/03-Grids.md). You can also use grids instead of columns. The main column is fully liquid, taking up all the rest of the space when the left column and right column have been rendered.

模板是用来解决页面布局的通用设计模式。可以使用模板来构建一个包含页眉、页脚、左右边栏和主体内容区域的页面。任何部分都可以通过[网格](https://github.com/bystep15/standard/blob/master/oocss/03-Grids.md)进行布局，也可以使用网格来代替竖栏布局。主体栏是流式布局，当左右边栏渲染完成后，主体栏会充满剩下的全部空间。

Please help me test the grids and template objects. Put them through their paces and let me know if you manage to break them!

请帮我测试网格和模板对象，测试它们的效果，如果出现问题，请联系我！

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
| `页面（page）` | 网站整页。它可以由`oldSchool`和`liquid`属性分别扩展为750px和全宽的布局。 |
| `页眉（head）` | 网站头部，通常包含自定义代码组成。（比如由水平导航栏，logo，搜索框）|
| `主体（body）` | 网站主体内容区域，是页面的主体部分。 |
| `页尾（foot）` | 网页尾部，通常包含自定义代码部分。 |
| `主要区域（main）` | 页面的主要内容区域，经常是中心栏。它全部是流式布局，会填充左右边栏渲染剩下的全部区域。您可以有一个主要的中心栏。 |
| `左边栏（leftCol）` | 左边栏，默认的宽度是250px。可以分别由`gMail`, `gCal`, `yahoo` 和 `myYahoo` 属性扩展为160px, 180px, 240px, 和 300px。您可以有0个到n个左边栏。 |
| `右边栏（rightCol）` | 右边栏，默认的宽度是250px。可以分别由`gMail`, `gCal`, `yahoo` 和 `myYahoo` 属性扩展为160px, 180px, 240px, 和 300px。您可以有0个到n个右边栏。 |
| `gMail` | 扩展`leftCol` 或 `rightCol`为160px的列宽。 |
| `gCal` | 扩展`leftCol` 或 `rightCol`为180px的列宽。 |
| `yahoo` | 扩展`leftCol` 或 `rightCol`为240px的列宽。 |
| `myYahoo` | 扩展`leftCol` 或 `rightCol`为300px的列宽。 |
| `oldSchool` | 扩展`page`为750px宽的布局。 |
| `liquid` | 扩展`leftCol`为全宽的流式布局。 |


## 基本模板（Basic template）
```html
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

## 全宽模板，两列，gmail格式类型（Full width template, 2 columns, gmail style （160px left column width））
```html
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

在面向对象的CSS中，最重要的目标是创建一个唯一的通用模板，可以用来构建所有页面。这会简化CMS的开发，因为从一个单页模板出发，可以构建成任何需要的页面。CMS用户也不必陷入一个单一页面没法变成不同页面类型的苦恼。面向对象的模板的另一个目标是每个部分（比如列，页头，等等）可以控制自身的变化。特别的是，如果您想向模板中添加一列左边栏，您唯一要做的就是向HTML中添加一列竖列，而不需要对着DOM，编写复杂的CSS样式完成需要的效果。循环整个DOM结构对于CMS的开发是很费事的。相似的，如果需要一个不一样的列宽，唯一需要做的就是给左列对象添加一个额外的类。

### 扩展一个对象（Extending an object）

```html
<div class="leftCol gMail"> ... </div>
```

## 制定模板（Customizing the template）

You may not find the default and extended widths of columns or pages match your site. In this case you can extend the column or main objects to allow custom widths. For performance reasons, you should avoid customizing templates whenever possible.

列宽度、页面宽度的默认和扩展可能跟您的站点不匹配，这种情况下可以通过继承列或者主体对象来实现自定义宽度。出于性能考虑，应该尽量避免自定义模板。

### 列（Columns）

`myColumn` extends column objects to allow for custom column widths.

`myColum`继承列对象，实现列宽度的自定义。

```css
.myColumn{width:400px;} 
```

### 主页（Main page）

`myPage`  extends `main`.

`myPage`继承`main`。

```css
.myPage{width:1050px !important;}
```

## 已知的问题（Known Issues）
- Source order - the right column is before the main content in the source order. This choice was made in order to allow the columns to be completely independent objects and to have one unique template rather than multiple starting points for a site. This speeds and simplifies CMS development and enhances usability for those creating pages within the CMS. Skip to content links and navigational items marked up as lists are strongly encouraged.

- 源码顺序 - 在源码中，右边栏的顺序应该在主体内容部分之前，目的是为了让边栏成为完全独立的对象，并且对于整个网站，从唯一的模板做起点开始编码，避免从多个不同的起点。这样可以加速和简化CMS的开发，并且提高页面的可用性。同时强烈建议把调转到内容区域的链接列表和导航列表用列表标记实现。

- Overflow - the containing blocks are made to wrap floats using the contexte de formattage; `overflow:hidden; _overflow:visible; zoom:1;`. This is known to cause printing bugs in older versions of Firefox and can cause absolutely positioned blocks originating in that container to be cropped. Removing floats and overflow via the print stylesheet is a corrective option.

- 溢出 - 包含块使用内容格式化的方式包含浮动块；`overflow:hidden; _overflow:visible; zoom:1;`。在老版本的Firefox中这会造成打印bug，并导致包含在该该块的绝对定位的块级元素被截短。针对这种情况，可以移除浮动和溢出，使用专门的打印样式表代替。
