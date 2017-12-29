# 模块 - 容器对象（Modules - Container Objects）

[原文](https://github.com/stubbornella/oocss/wiki/Module)

Modules are based on the [Standard Module Format](https://github.com/bystep15/standard/blob/master/oocss/04-Standard-Module-Format.md). They provide a simple, predictable way to skin container objects while maintaining accessibility and performance. Contour skins are separate from background skins, headers, and footers. I suggest you name skins in a way that indicates how that skin should be used (semantically). The module skin should not change the display of objects within its open editable zones. Features include: 

模块基于[标准模块格式](https://github.com/bystep15/standard/blob/master/oocss/04-Standard-Module-Format.md)。它们为渲染容器对象提供了一个简单的，可预测的方法，同时保持可访问性和性能。轮廓区域的渲染独立于背景，页眉和页尾的渲染。在这里我认为您命名渲染的表现形式在某种程度上应该是表示渲染是如何使用的（基于语义上来命名）。渲染的模块不应该改变该对象在其开放的可编辑区域内的表现。包含的特性有以下几点：

-  Less than 2K! (structures)
-  Simple to skin
-  One image per module
-  Height and width agnostic
-  Accessibility and performance baked-in
-  Separates semantic markup from presentational fluff


- 小于2K（结构上）
- 容易渲染
- 每个模块一张图片
- 高度和宽度未知
- 无障碍且表现出色
- 将语义与表现相分离

## Base Classes
| Property | Description |
| --------- |---------|
| `mod` | Base class for all container modules. Use `mod` unless you specifically need one of the other structure objects. Mod is transparent on the inside, corners overlay content, it can therefore be used with any content. Allows infinite height and width as borders are generated via skin objects that define borders on `mod` and `inner`.  |
| `complex` | Extends `mod`. Allows full image borders for cases where the desired look and feel cannot be generated via borders on `mod` and `inner`. `complex` is transparent on the inside, corners overlay content, thus it can be used with any content.  |
| `pop` | Extends `mod`. Allows transparent outside, such as drop shadows. Use in cases where the module overlays an image, text, or other variable background. `pop` is transparent on the outside, content overlays background, thus it cannot be used with any content  |
| `top` | A presentational element which wraps the top corners. It is used by `complex` to display the upper edge of the block. In other block structures it has no height. This empty, non-semantic element should be inserted via a serverside script or JavaScript, the former is preferable.  |
| `bottom` | A presentational element which wraps the bottom corners. It is used by `complex` to display the lower edge of the block. In other block structures it has no height. This empty, non-semantic element should be inserted via a serverside script or JavaScript, the former is preferable.  |
| `tl` | A presentational element used to display the top left corner of a block, and in `complex` the left edge of the block. This empty, non-semantic element should be inserted via a serverside script or JavaScript, the former is preferable.  |
| `tr` | A presentational element used to display the top right corner of a block, and in `complex` the right edge of the block. This empty, non-semantic element should be inserted via a serverside script or JavaScript, the former is preferable.  |
| `bl` | A presentational element used to display the bottom left corner of a block. This empty, non-semantic element should be inserted via a serverside script or JavaScript, the former is preferable.  |
| `br` | A presentational element used to display the bottom right corner of a block. This empty, non-semantic element should be inserted via a serverside script or JavaScript, the former is preferable.  |

| 属性 | 描述 |
| --------- |---------|
| `mod` | 所有容器模块的基本类型。除非您特别地需要使用其他结构对象，否则请您使用`mod`。Mod属性在内部，角落和覆盖内容上是透明的，因此可以用在任何区域上。边框是渲染对象通过`mod` 和 `inner`属性来定义的，并且可以使用无线长的高度和宽度。 |
| `complex` | 由`mod`.扩展而来。在无法通过`mod`和`inner`的边框生成所需外观的情况下，允许使用全图像边框。`complex`在内部，角落和覆盖内容上是透明的，因此可以用在任何区域上。 |
| `pop` | 由`mod`.扩展而来。允许使用透明的外边框，就像下落的阴影。在模块覆盖图像，文本或其他可变背景的情况下使用。`pop`在外边框，内容覆盖掉背景的情况下是透明的，因此不能用在任何地方。 |
| `top` | 是一个用来描述顶角的表现元素。它通过使用`complex`元素来表现块的上边缘。在其他的块级元素中，它没有高度。这种空的，没有表现性的元素应该被嵌入到服务端脚本和JavaScript，更推荐前一种方式。 |
| `bottom` | 是一个用来描述底角的表现元素。它通过使用`complex`元素来表现块的下边缘。在其他的块级元素中，它没有高度。这种空的，没有表现性的元素应该被嵌入到服务端脚本和JavaScrip，更推荐前一种方式。 |
| `tl` | 是一个用来描述块的左上角和`complex`中块的左边缘的表现元素。这种空的，没有表现性的元素应该被嵌入到服务端脚本和JavaScrit，更推荐前一种方式。 |
| `tr` | 是一个用来描述块的右上角和`complex`中块的右边缘的表现元素。这种空的，没有表现性的元素应该被嵌入到服务端脚本和JavaScrit，更推荐前一种方式。 |
| `bl` | 是一个用来描述块的左下角的表现元素。这种空的，没有表现性的元素应该被嵌入到服务端脚本和JavaScrit，更推荐前一种方式。 |
| `br` | 是一个用来描述块的右下角的表现元素。这种空的，没有表现性的元素应该被嵌入到服务端脚本和JavaScrit，更推荐前一种方式。 |

## 标记（The Markup）

### 模块属性（Module）

Mod is the basic container, all other containers inherit from this one. This is the high performance container that should be used unless you specifically need another type.

Mod是一种基本的容器。所有其他的容器都是继承自它。它是一种具有高表现性的容器，所以除非您需要另外使用其他的样式，您都应当使用它。

- 一张小图片
- 可以扩展成任意的宽度和高度
- 与任何内容兼容
- 可以选择任何不需要外部透明度或复杂边界的容器对象。

- One tiny image
- Expands to any height or width
- Compatible with any content
- Choose for any container object that doesn't require outside transparency or complex borders.

```
<div class="mod"> 
        <b class="top"><b class="tl"></b><b class="tr"></b></b>
	<div class="inner">
		<div class="bd">
			<p>Lorem ipsum.</p>
		</div>
	</div>
	<b class="bottom"><b class="bl"></b><b class="br"></b></b> 
</div>

```
### 复杂属性（Complex）

Complex should be used in cases where you require images for borders because borders or drop shadows are too complex to be simulated via borders on mod and/or inner.

复杂属性（complex）应当被用在当您需要对边框使用照片的时候。因为使用mod属性和（或者）inner属性来模拟边框和下落的阴影过于复杂，所以推荐使用complx属性。

- One image
- Height and width limited by image size
- Compatible with any content
- Choose when you require complex borders which cannot be simulated via css borders on mod and inner.

- 一张图片
- 高度和宽度只限于图片的大小
- 与任何内容兼容
- 当您需要使用复杂的边框且无法通过mod和inner属性下的css边框来实现。

Inspired by a conversation with Arnaud.

这些内容是受到Arnaud的启发产生的想法。

```
<div class="mod complex"> 
        <b class="top"><b class="tl"></b><b class="tr"></b></b>
	<div class="inner">
		<div class="bd">
			<p>Lorem ipsum.</p>
		</div>
	</div>
	<b class="bottom"><b class="bl"></b><b class="br"></b></b> 
</div>
```

### 弹出属性（Popup）

Use for popups and other containers that need outside transparency.

用于需要外部透明度的弹出窗口和其他容器。

- One image
- Height and width limited by image size
- Compatible with any container, but not any content
- Choose when you require outside transparency which cannot be simulated. (do i need to make this work with clip rather than bkg position?)

- 一张图片
- 高度和宽度只限于图片的大小
- 与任何容器兼容，但并不是与任何内容兼容
- 当您需要使用无法模拟的外部透明度时使用（我应该使用剪辑而不是bkg的方式来做这项工作？）

Inspired by Leslie Sommers mojo blocks.

这些内容是受到Leslie Sommers mojo blocks启发产生的想法。

```
<div class="mod pop"> 
        <b class="top"><b class="tl"></b><b class="tr"></b></b>
	<div class="inner">
		<div class="bd">
			<p>Lorem ipsum.</p>
		</div>
	</div>
	<b class="bottom"><b class="bl"></b><b class="br"></b></b> 
</div>
```

## 渲染时的一些建议（Skinning suggestions）
The contour and the background can be used to define the intersection of two parameters. For example you cross product status with product type. E.g. `sale`, `normal`, and `featured` backgrounds with `motorcycle`, `helmet`, and `clothing` contours. In so far as possible, keep your classes as abstract as they can reasonably be. For example choose `motorcycle` over `ducati`, `ducatiMonster`, or `NicolesDucatiMonster620dark` -- unless you really mean to exclude all other uses! 

轮廓和背景可以用来定义两个参数的交集。例如，当您使用产品类型例如sale`, `normal`和`featured`的背景属性和`motorcycle`, `helmet`和`clothing`的轮廓属性来描述您的产品状态时。请让您的类尽可能抽象。例如选择使用`motorcycle`属性而不是`ducati`, `ducatiMonster`和 `NicolesDucatiMonster620dark` -- 当然，除非您真的不想用它们其他的所有用途！

Be careful not to choose classes linked to the display of the object (e.g. big blue borders).  The client will change their mind, you'll have classes which no longer correlate to actual display.

当心！不要选择与对象表现形式相关的类（例如 big，blue，borders等与表现相关的类）。这样做会改变这些类的初衷，如果您这样做，这些类的使用将会与它们的实际表达效果不相关。

## 当您选用模块时如何决定（How to decide when to use Modules）

Deciding when to use Modules can be confusing. As a rule of thumb, if you are marking up an element on the page that conveys relevant information to the user by itself (e.g. breadcrumbs), you do not need a module. This is a good example for a content object. However, if you are marking up a container that conveys no relevant information on its own (e.g. tabs) and would only make sense to use when you place content objects in it, then you could mark it up as a module.

也许当您使用模块时会感到困惑。从经验上讲，如果您在页面上标记的元素可以向用户传递相关信息时（例如面包屑breadcrumb），您不必使用模块。对于内容对象来说，这是一个很好的例子。但是，如果您在标记一个传递与其本身信息无关的容器时（就像标签tabs）并且只有当您将其中的元素换用内容对象才符合意义时，那您可以将它标注为一个模块。

So you could ask "Is this element conveying any relevant information to the user?". A container is never useful information to the user on its own; only the content elements within it convey reasonable information to the user. So if your answer to the question is "No", you could use a module.

所以，您可以这样问：“这个元素是否向用户传递了相关的信息呢？”一个容器本身绝对不会为用户提供有用的信息；只有里面的内容元素可以向用户传递相关的信息。所以，如果您的回答是“No”，那您可能再用一个模块。

## Thanks
Great feedback, bug reports,etc. Chris Griego, Jordan LaMons, Arnaud Gueras (as usual), Ryan Grove, Nicholas Zakas, Peter Ellenhauge, Chris Eppstein, Vinod Kerkar, Carsten, Dan H, Cindy Li, etc.


32/5000
感谢以下人员提供的良好的反馈意见和错误报告等。Chris Griego, Jordan LaMons, Arnaud Gueras (as usual), Ryan Grove, Nicholas Zakas, Peter Ellenhauge, Chris Eppstein, Vinod Kerkar, Carsten, Dan H, Cindy Li等。
