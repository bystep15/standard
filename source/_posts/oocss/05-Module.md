title: 05、模块 - 容器对象（Modules - Container Objects）
categories: [理论, css, oocss]
tags: [理论, css, oocss]
date: 2018/06/26 09:30:00
---

[原文](https://github.com/stubbornella/oocss/wiki/Module)
[示例](http://oocss.org/module.html)

Modules are based on the [Standard Module Format](/standard/2018/06/06/04、标准模块格式（standard-module-format）.html). They provide a simple, predictable way to skin container objects while maintaining accessibility and performance. Contour skins are separate from background skins, headers, and footers. I suggest you name skins in a way that indicates how that skin should be used (semantically). The module skin should not change the display of objects within its open editable zones. Features include: 

-  Less than 2K! (structures)
-  Simple to skin
-  One image per module
-  Height and width agnostic
-  Accessibility and performance baked-in
-  Separates semantic markup from presentational fluff


基于[标准模块格式](/standard/2018/06/06/04、标准模块格式（standard-module-format）.html)的模块，提供了一个简单、可预测的皮肤容器，同时保持可访问性和性能。轮廓皮肤，背景皮肤，页眉和页尾分别独立。建议基于使用来对皮肤进行命名（语义化）。模块皮肤不应该改变其内部对象的显示。支持以下特性：

- 小于2K（结构上）
- 定制皮肤简单
- 每个模块一张图片
- 高度和宽度无关
- 不影响可访问性和性能
- 分离语义与外观

## 基础类（Base Classes）

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
| `mod` | 所有容器模块的基类。大多数情况下使用`mod`即可，除非需要使用其他特定结构对象。Mod背景透明，边角覆盖在内容之上，因此可以和任何内容用在一起。通过在`mod` 和 `inner`上定义皮肤样式，可以支持长度的高度和宽度。 |
| `complex` | 扩展`mod`。在无法通过`mod`和`inner`的边框生成所需外观的情况下，允许使用全图像边框。`complex`背景透明，边角覆盖在内容之上，因此可以和任何内容用在一起。 |
| `pop` | 扩展`mod`。允许使用透明的外边框，比如投影。在模块包含图像，文本或其他可变背景的情况下使用。`pop`外边框是透明的，内容覆盖在背景上，因此不能用在任何地方。 |
| `top` | 一个用来包裹顶角的表现元素。使用`complex`时表现为块的上边缘。在其他的块级元素中，它没有高度。这种空的，没有语义的元素应该由服务端脚本和JavaScript嵌入，推荐前一种方式（笔者按：Server插入或JavaScript插入都不可取，既然需要，简单直接表明）。|
| `bottom` | 一个用来包裹底角的表现元素。使用`complex`时表现为块的下边缘。在其他的块级元素中，它没有高度。这种空的，没有语义的元素应该由服务端脚本和JavaScript嵌入，推荐前一种方式（笔者按：Server插入或JavaScript插入都不可取，既然需要，简单直接表明）。|
| `tl` | 一个用来渲染左上角或`complex`中左边缘的块级表现元素。这种空的，没有语义的元素应该由服务端脚本和JavaScript嵌入，推荐前一种方式（笔者按：Server插入或JavaScript插入都不可取，既然需要，简单直接表明）。|
| `tr` | 一个用来渲染右上角或`complex`中右边缘的块级表现元素。这种空的，没有语义的元素应该由服务端脚本和JavaScript嵌入，推荐前一种方式（笔者按：Server插入或JavaScript插入都不可取，既然需要，简单直接表明）。|
| `bl` | 一个用来渲染左下角的块级表现元素。这种空的，没有语义的元素应该由服务端脚本和JavaScript嵌入，推荐前一种方式（笔者按：Server插入或JavaScript插入都不可取，既然需要，简单直接表明）。|
| `br` | 一个用来渲染右下角的块级表现元素。这种空的，没有语义的元素应该由服务端脚本和JavaScript嵌入，推荐前一种方式（笔者按：Server插入或JavaScript插入都不可取，既然需要，简单直接表明）。|

## 标记（The Markup）

### 模块类（Module）

Mod is the basic container, all other containers inherit from this one. This is the high performance container that should be used unless you specifically need another type.

- One tiny image
- Expands to any height or width
- Compatible with any content
- Choose for any container object that doesn't require outside transparency or complex borders.

Mod是基本容器，其他所有的容器都继承自它。这是一种具有高表现性的容器，所以除非您需要另外使用其他的样式，您都应当使用它。

- 一张小图片
- 支持任意的宽度和高度
- 兼容任何内容
- 适用于不需要外部透明度或复杂边界的容器对象。

```html
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
### 复杂类（Complex）

Complex should be used in cases where you require images for borders because borders or drop shadows are too complex to be simulated via borders on mod and/or inner.

- One image
- Height and width limited by image size
- Compatible with any content
- Choose when you require complex borders which cannot be simulated via css borders on mod and inner.


复杂类（complex）被用在需要图片边框的时候，此时使用mod属性和（或者）inner属性来描述边框和下落的阴影过于复杂，所以推荐使用complx类。

- 一张图片
- 高度和宽度受限于图片尺寸
- 兼容任何内容
- 当需要使用复杂的边框，并且无法通过mod和inner类下的css边框来实现的时候。

Inspired by a conversation with Arnaud.

这些内容是受到Arnaud的启发产生的想法。

```html
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

### 弹出类（Popup）

Use for popups and other containers that need outside transparency.

- One image
- Height and width limited by image size
- Compatible with any container, but not any content
- Choose when you require outside transparency which cannot be simulated. (do i need to make this work with clip rather than bkg position?)


用于需要外部透明度的弹出窗口和其他容器。

- 一张图片
- 高度和宽度受限于图片尺寸
- 兼容任何容器，但不一定兼容任何内容
- 当需要使用无法模拟的外部透明效果时使用（是否使用clip而不是bkg定位的方式更合适？）

Inspired by Leslie Sommers mojo blocks.

这些内容是受到Leslie Sommers mojo blocks启发产生的想法。

```html
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

## 皮肤使用建议（Skinning suggestions）

The contour and the background can be used to define the intersection of two parameters. For example you cross product status with product type. E.g. `sale`, `normal`, and `featured` backgrounds with `motorcycle`, `helmet`, and `clothing` contours. In so far as possible, keep your classes as abstract as they can reasonably be. For example choose `motorcycle` over `ducati`, `ducatiMonster`, or `NicolesDucatiMonster620dark` -- unless you really mean to exclude all other uses! 

轮廓和背景可以定义成两个类组合使用。例如，当需要联合使用产品状态和产品类型的时候。例如`sale`, `normal`和`featured`的背景类和`motorcycle`, `helmet`和`clothing`的轮廓类组合。保持类尽可能合理的抽象。例如选择使用`motorcycle`属性而不是`ducati`, `ducatiMonster`和 `NicolesDucatiMonster620dark` -- 当然，除非您真的不想将它们复用！

Be careful not to choose classes linked to the display of the object (e.g. big blue borders).  The client will change their mind, you'll have classes which no longer correlate to actual display.

当心！不要使用与对象表现形式相关的类名（例如 big，blue，borders）。客户会改变想法，代码中会存在一批与实际表达效果不相符的类。

## 何时使用模块（How to decide when to use Modules）

Deciding when to use Modules can be confusing. As a rule of thumb, if you are marking up an element on the page that conveys relevant information to the user by itself (e.g. breadcrumbs), you do not need a module. This is a good example for a content object. However, if you are marking up a container that conveys no relevant information on its own (e.g. tabs) and would only make sense to use when you place content objects in it, then you could mark it up as a module.

也许当您使用模块时会感到困惑。从经验上讲，如果您在页面上标记的元素可以向用户传递相关信息时（例如面包屑breadcrumb），您不必使用模块。对于内容对象来说，这是一个很好的例子。但是，如果您在标记一个传递与其本身信息无关的容器时（就像标签tabs）并且只有当您将其中的元素换用内容对象才符合意义时，那您可以将它标注为一个模块。

So you could ask "Is this element conveying any relevant information to the user?". A container is never useful information to the user on its own; only the content elements within it convey reasonable information to the user. So if your answer to the question is "No", you could use a module.

所以，您可以这样问：“这个元素是否向用户传递了相关的信息呢？”一个容器本身绝对不会为用户提供有用的信息；只有里面的内容元素可以向用户传递相关的信息。所以，如果您的回答是“No”，那您可能再用一个模块。

## Thanks
Great feedback, bug reports,etc. Chris Griego, Jordan LaMons, Arnaud Gueras (as usual), Ryan Grove, Nicholas Zakas, Peter Ellenhauge, Chris Eppstein, Vinod Kerkar, Carsten, Dan H, Cindy Li, etc.


感谢以下人员提供的良好的反馈意见和错误报告等。Chris Griego, Jordan LaMons, Arnaud Gueras (as usual), Ryan Grove, Nicholas Zakas, Peter Ellenhauge, Chris Eppstein, Vinod Kerkar, Carsten, Dan H, Cindy Li等。
