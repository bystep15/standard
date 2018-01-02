# 模块的表现形式（Module Skins）

[原文](https://github.com/stubbornella/oocss/wiki/Module-Skins)

Each of the three module types needs to be skinned differently.  Abstracting all the heavy lifting to the `mod`, `complex`, and `pop` classes means that all of the values in the skins are predictable. In fact, I'll show you how they can be easily calculated.

三种模块类型的渲染形式都有所不同。将所有关键的东西抽象到`mod`, `complex`, 和 `pop`中意味着所有渲染结果的值都是可以预测的。事实上，我将会为您展示它们是如何可以简单地计算得到结果的。

## 扩展模块（Extending mod）

Let's create a simple grey rounded corner box.

让我们来创建一个简单的灰色的圆角盒子。

```
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


```
/* ----- simple (extends mod) ----- */
.simple .inner {border:1px solid #D7D7D7;-moz-border-radius: 7px;-webkit-border-radius: 7px;border-radius: 7px;}
.simple b{*background-image:url(skin/mod/simple_corners.png);}
```

1. We define the border to be one pixel solid gray. Anytime only one border is used it should be placed on `inner` rather than the module itself (to simplify the skin). 
2. We then tell browsers that the module should have rounded corners.
3. Internet Explorer 5.5, 6, 7, 8 do not support rounded corners. Line two provides an image backup to generate these corners. The star hack is used so that better browsers that natively support rounded corners do not download the extra image unnecessarily.  You may also choose to omit this line and provide a square corner fallback for IE depending on how much market share they have amongst your visitors.

1. 我们定义一个1像素的实体灰色边框。任何时候如果只有一个边框被使用，那么它应该放在`inner`中而不是该模块本身（以简化渲染）。
2. 然后我们告诉浏览器这个模块应该有圆角。
3. IE 5.5,6,7,8不支持圆角。样式中第二行提供了照片备份来生成这些圆角。样式代码中星标被用来表示当浏览器支持原生的圆角时就不会下载额外的图片。您也许会选择省略掉该行并为IE提供一个方形的角落回退，这取决于使用IE的访客在所有用户中拥有多少市场份额。

## 复杂属性（complex）

## pop
