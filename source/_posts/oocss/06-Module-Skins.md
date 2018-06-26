title: 06、模块皮肤（Module Skins）
categories: [理论, css, oocss]
tags: [理论, css, oocss]
date: 2018/06/26 18:30:00
---

[原文](https://github.com/stubbornella/oocss/wiki/Module-Skins)

Each of the three module types needs to be skinned differently.  Abstracting all the heavy lifting to the `mod`, `complex`, and `pop` classes means that all of the values in the skins are predictable. In fact, I'll show you how they can be easily calculated.

三种类型模块的皮肤需要不同的设置方法。将所有繁重的工作抽象到`mod`, `complex`, 和 `pop`3个类中，意味着所有皮肤的值都是可以预测的。接下来，我将会为您展示它们是如何通过简单地计算得到的。

## 扩展模块（Extending mod）

Let's create a simple grey rounded corner box.

让我们来创建一个简单的灰色圆角盒子。

```html
<div class="mod simple"> 
    <b class="top"><b class="tl"></b><b class="tr"></b></b> 
    <div class="inner">
        <div class="hd">
            <h3>simple</h3>
        </div>
        <div class="bd">
            <p>Body</p>
        </div>
    </div>
    <b class="bottom"><b class="bl"></b><b class="br"></b></b> 
</div>
```


```css
/* ----- simple (extends mod) ----- */
.simple .inner {
    border: 1px solid #D7D7D7;
    -moz-border-radius: 7px;
    -webkit-border-radius: 7px;
    border-radius: 7px;
}
.simple b {
    *background-image:url(skin/mod/simple_corners.png);
}
```

1. We define the border to be one pixel solid gray. Anytime only one border is used it should be placed on `inner` rather than the module itself (to simplify the skin). 
2. We then tell browsers that the module should have rounded corners.
3. Internet Explorer 5.5, 6, 7, 8 do not support rounded corners. Line two provides an image backup to generate these corners. The star hack is used so that better browsers that natively support rounded corners do not download the extra image unnecessarily.  You may also choose to omit this line and provide a square corner fallback for IE depending on how much market share they have amongst your visitors.


1. 首先定义一个1像素的实体灰色边框。任何时候如果只有一个边框被使用，那么应该把它放在`inner`中而不是模块本身（以简化皮肤样式）。
2. 然后声明模块应该有圆角。
3. IE 5.5,6,7,8不支持圆角。第二段样式中用图片做降级方案来生成圆角。样式代码中使用星号Hack方法，指示更高版本的支持原生圆角的浏览器不会下载额外的图片。也可以选择省略掉该段代码，IE上显示为一个方形的角落，这取决于使用IE的用户占比。

## 复杂类（complex）

## pop
### Todo
