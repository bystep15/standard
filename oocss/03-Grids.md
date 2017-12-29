# Grids

[原文](https://github.com/stubbornella/oocss/wiki/Grids)

Grids are used to break any space into fractions, they can be nested and stacked. A unit can contain another line or it can contain other objects directly.  The sum of the fractional sizes of all children of one line should be equal to one. Grids control width, content controls height. The grids have all the functionality of YUI grids and some other important features.

网格经常用来将任何空间打碎成碎片，这些碎片可以被嵌套和堆叠。一个单元可以直接包含另一行或者其他的元素。一行中的所有内容的碎片空间总和应当等于其他一行的空间。网格控制着宽度，内容控制着高度。网格元素拥有YUI网格中所有的功能和一些其他重要的特性。

- Less than 1kb! (including full templates and grids)
- Infinite nesting and stacking.
- The only change required to use any of the objects, is to place it in the HTML. No changes to other places in the DOM, and no location dependent styling. 
- Easy integration with back-end development.
- Easy for beginners to create complex page layouts.




- 小于1kb！（包含所有的模板和网格）
- 可以无限地嵌套和堆叠。
- 使用不同对象的唯一的变化是将不同的对象放到HTML中。在DOM中没有其他地方要改变，并且没有为独立样式提供位置。
- 对后端的开发进行了简单的整合。
- 对于初学者创建复杂页面布局提供了简单的方法。

Please help me test the grids and template objects. Put them through their paces and let me know if you manage to break them!

请帮我测试网格和模板对象。请您测试它们的效果，如果您设法去改变这样的用法，请您联系我！

## Base Classes
| Property | Description |
| --------- |---------|
| `line` | Groups units on one horizontal line. Note: for mobile layout units may be stacked to avoid horizontal scrolling.  |
| `unit` | Base class which divides a line into sections (columns).  |
| `sizeXofY` | Extends `unit`. Indicates the fractional width of the unit, for example `size3of4` would take up three quarters, or 75%, of the horizontal space. The following fractions are supported: 1, 1/2, 1/3, 2/3, 1/4, 3/4, 1/5, 2/5, 3/5, 4/5  |
| `lastUnit` | Extends `unit`. Applied to the last child of every line.  |


| 属性 | 描述 |
| --------- |---------|
| `行(line)` | 一组网格单元位于一条水平的行上。注意：对于移动端布局单元来说，网格单元可能会被堆积以避免水平滚动。 |
| `单元（unit）` | 将一行分为几个部分（列）的基本类。 |
| `sizeXofY` | 扩展于`unit`。表明单元极小的宽度，例如，`size3of4`可能占据整个水平空间的四分之三，或者75%。支持的分数形式如下：1, 1/2, 1/3, 2/3, 1/4, 3/4, 1/5, 2/5, 3/5, 4/5。 |
| `最后一个单元（lastUnit）` | 扩展于`unit`. 应用于每行中最后一个子元素。 |


[在Flickr上，由Stubbornella提出的网格上可能用到的OOCSS框架(Grids possible with OOCSS framework by Stubbornella (aka Nicole), on Flickr)](http://www.flickr.com/photos/nicole_hugo/3291743394/)

![Grids possible with OOCSS framework](http://farm4.static.flickr.com/3460/3291743394_4f4041bce5_b.jpg)

## 一半（Halves）

```
<div class="line">
	<div class="unit size1of2">
		<h3>1/2</h3>
		<p>Lorem ipsum dolor sit amet...</p>
	</div>
	<div class="unit size1of2 lastUnit">
		<h3>1/2</h3>
		<p>Lorem ipsum dolor sit amet...</p>
	</div>
</div>
```

## 三等分（Thirds）

### 1/3, 1/3, 1/3

```
<div class="line">
	<div class="unit size1of3">
		<h3>1/3</h3>
		<p>Lorem ipsum dolor sit amet...</p>
	</div>
	<div class="unit size1of3">
		<h3>1/3</h3>
		<p>Lorem ipsum dolor sit amet...</p>
	</div>
	<div class="unit size1of3 lastUnit">
		<h3>1/3</h3>		
		<p>Lorem ipsum dolor sit amet...</p>
	</div>
</div>
```

### 1/3, 2/3

```
<div class="line">
	<div class="unit size1of3">
		<h3>1/3</h3>
		<p>Lorem ipsum dolor sit amet...</p>
	</div>
	<div class="unit size2of3 lastUnit">
		<h3>2/3</h3>
		<p>Lorem ipsum dolor sit amet...</p>
	</div>
</div>
```

## 四等分（Quarters）

### 1/4, 1/4, 1/2

```
<div class="line">
	<div class="unit size1of4">
		<h3>1/4</h3>
		<p>Lorem ipsum dolor sit amet...</p>
	</div>
	<div class="unit size1of4">
		<h3>1/4</h3>
		<p>Lorem ipsum dolor sit amet...</p>
	</div>
	<div class="unit size1of2 lastUnit">
		<h3>1/2</h3>
		<p>Lorem ipsum dolor sit amet...</p>
	</div>
</div>
```

### 3/4, 1/4

```
<div class="line">
	<div class="unit size3of4">
		<h3>3/4</h3>
		<p>Lorem ipsum dolor sit amet...</p>
	</div>
	<div class="unit size1of4 lastUnit">
		<h3>1/4</h3>
		<p>Lorem ipsum dolor sit amet...</p>
	</div>
</div>
```

## 五等分（Fifths）

### 4/5, 1/5

```
<div class="line">
	<div class="unit size4of5">
		<h3>4/5</h3>
		<p>Lorem ipsum dolor sit amet...</p>
	</div>
	<div class="unit size1of5 lastUnit">
		<h3>1/5</h3>
		<p>Lorem ipsum dolor sit amet...</p>
	</div>
</div>
```

### 2/5, 3/5

```
<div class="line">
	<div class="unit size2of5">
		<h3>2/5</h3>
		<p>Lorem ipsum dolor sit amet...</p>
	</div>
	<div class="unit size3of5 lastUnit">
		<h3>3/5</h3>
		<p>Lorem ipsum dolor sit amet...</p>
	</div>
</div>
```

## 复杂的集合 - AG测试（Complicated Nesting - the AG test）

[在Flickr上，由Stubbornella (aka Nicole)设计的基于大型的网格系统的AG测试（AG test of a great grids system by Stubbornella (aka Nicole), on Flickr）](http://www.flickr.com/photos/nicole_hugo/3291776052/)

![AG test of a great grids system](http://farm4.static.flickr.com/3549/3291776052_b7c8f36ed9.jpg)

Many years ago Arnaud Gueras, an excellent developer I worked with, created this litmus of a great grids system.  It should be able to nest any combination of the units and lines, and so it should be able to create the complicated layout below.  His test reminded me of the golden mean, so I still use it today. 

许多年前，一个跟我一起工作的杰出的开发者Arnaud Gueras创建一个完美的网格系统。它应当可以实现聚集所有单元和行的结合，并且可以创建一个复杂的布局结构。他的测试为我提供了这个完美的想法，并且我一直沿用至今。

```
<div class="line">
	<div class="unit size1of5">
		<h3>1/5</h3>
		<p>Lorem ipsum dolor sit amet...</p>
		<p>Lorem ipsum dolor sit amet...</p>
		<p>Lorem ipsum dolor sit amet...</p>
	</div>
	<div class="unit size3of5">
		<!-- line -->
		<div class="line">
			<div class="unit size1of2">
				<h3>1/2</h3>
				<p>Lorem ipsum dolor sit amet...</p>
			</div>
			<div class="unit size1of2 lastUnit">
				<h3>1/2</h3>
				<p>Lorem ipsum dolor sit amet...</p>
			</div>
		</div>
		<!-- /line -->
		<div class="line">
			<div class="unit size1of3">
				<h3>1/3</h3>
				<p>Lorem ipsum dolor sit amet...</p>
                                <p>Lorem ipsum dolor sit amet...</p>
			</div>
			<div class="unit size2of3 lastUnit">
				<!-- line -->
				<div class="line">
					<div class="unit size1of2">
						<h3>1/2</h3>
						<p>Lorem ipsum dolor sit amet...</p>
					</div>
					<div class="unit size1of2 lastUnit">
						<h3>1/2</h3>
						<p>Lorem ipsum dolor sit amet...</p>
					</div>
				</div>
				<!-- /line -->
				<div class="line">
					<div class="unit size1of1">
						<h3>1</h3>
						<p>Lorem ipsum dolor sit amet...</p>
					</div>
				</div>
			</div>
		</div>
	</div>
	<div class="unit size1of5 lastUnit">
		<h3>1/5</h3>
		<p>Lorem ipsum dolor sit amet...</p>
		<p>Lorem ipsum dolor sit amet...</p>
		<p>Lorem ipsum dolor sit amet...</p>
	</div>
</div>
```
