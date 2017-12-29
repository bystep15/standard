#标准模块格式（Standard Module Format）

[原文](https://github.com/stubbornella/oocss/wiki/Standard-Module-Format)

The standard module format is based on the [YUI module control](http://developer.yahoo.com/yui/examples/container:/module.html).  I hope to include input from microformats and HTML5 communities to inform the choice of class names.

标准的模块布局是基于[YUI模块控制](http://developer.yahoo.com/yui/examples/container:/module.html)。我希望从微格式和HTML5社区中为类获取合适的类名。

| Property | Description |
| --------- |---------|
| `mod` | Module is the wrapper for every container object. It provides basic structure for a transparent inside module. It can be extended by `mojo` or `ag`to provide for transparent outside and complex borders respectively.  |
| `inner` | Inner exists for two reasons. First, it solves a bug (Opera prior to version 8.5) in which position relative and overflow hidden cannot exist on the same element. Second, it allows for two elements on which borders can be placed to extend the number of blocks that can be built without using image based borders.  |
| `hd` | The module header generally contains a heading, but may also contain buttons, links, tabs, etc. `hd` provides basic structure and can be extended via skin classes. A module can have 0-1 (should this be 0-n?) `hd`.  |
| `bd` | The body is the main open editable region of the module. It is an obligatory region, the module may contain 1-n bodies.  |
| `ft` | The module footer is an object. ft provides basic structure and it can be extended via skin classes.  |

| 属性 | 描述 |
| --------- |---------|
| `mod` | 模块是任何容器对象的承载体。它为透明的内在模块提供了基本的结构。它可以由`mojo` 或者 `ag`各自扩展成透明的外边距和复杂的边框。 |
| `inner` | 内元素（inner）存在有两个原因。第一，它解决了一个bug（存在于早于8.5版本的Opera浏览器），这个bug是相对定位和溢出隐藏没办法同时存在于一个元素上。第二，它允许使用两个元素的边框来扩展块的数量，而不使用基于图像的边界来扩展。 |
| `hd` | 这个模块头通常包括一个标题，也可以包含按钮，链接，标签等等。`hd`提供了基本的结构并且可以通过皮肤类（skin classes）来扩展。一个模块中可以包含0~1（或者说0~n？）个`hd`。 |
| `bd` | 主体部分是模块中主要的开放可编辑的区域。它是必须存在的区域，模块可以包含1~n个主体部分。 |
| `ft` | 这个尾部模块是一个对象。`ft`提供了基本的结构并且可以由皮肤类（skin classes）来扩展。 |

```
<div class="mod">
	<div class="inner">
		<div class="hd">head</div>
		<div class="bd">body</div>
		<div class="ft">foot</div>
	</div>
</div>
```
