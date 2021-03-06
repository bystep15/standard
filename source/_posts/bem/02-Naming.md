title: 02、命名（Naming）
categories: [理论, css, bem]
date: 2018/06/28 21:30:00
tags: [理论, css, bem]
---

[原文](http://getbem.com/naming/)

> There are only two hard problems in Computer Science: cache invalidation and naming things — *Phil Karlton*

> 计算机科学中有两个最难的问题：缓存失效和命名 - *Phil Karlton*

It is a known fact that the right styleguide can significantly increase development speed, debugging, and the implementation of new features in legacy code. Sadly, most CSS codebases are sometimes developed without any structure or naming conventions. This leads to an unmaintainable CSS codebase in the long term.

一个众所周知的事实：正确的编码风格可以显著地提高开发、调试以及在遗留代码添加新功能的速度。令人遗憾的是，大多数CSS代码库是在没有任何结构约定或命名约定的情况下开发的。这种导致了CSS代码库长期不可维护。

The BEM approach ensures that everyone who participates in the development of a website works with a single codebase and speaks the same language. Using proper naming will prepare you for the changes in design of the website.

BEM的方法确保参与网站开发的每个人都可以使用单一的代码库，并使用共同的语言进行开发。同时为将来网站的变化提供了适当的命名规范。

### 块（Block）

Encapsulates a standalone entity that is meaningful on its own. While blocks can be nested and interact with each other, semantically they remain equal; there is no precedence or hierarchy. Holistic entities without DOM representation (such as controllers or models) can be blocks as well.

块是封装为一个独立有意义的实体。虽然块可以相互嵌套和交互，但是在语义上，它们是平等的，没有优先级或层级区分。注意，即使没有DOM的完整实体（如控制器或模型）也可以是一个块。

##### 命名（Naming）

Block names may consist of Latin letters, digits, and dashes. To form a CSS class, add a short prefix for namespacing: `.block`

块的命名可以包括拉丁字母，数字和中横线组成。为了构成一个CSS类，需要在命名空间上添加一个简短的前缀`.block`。

##### HTML

Any DOM node can be a block if it accepts a class name.

任何DOM节点如何可以接收到一个类名，都可以成为一个块元素。

```html
<div class="block">...</div>
```

##### CSS

* Use class name selector only
* No tag name or ids
* No dependency on other blocks/elements on a page


* 仅使用类选择器
* 不包含标签名称或ID
* 不依赖页面上的其他块/元素

```css
.block { color: #042; }
```

### 元素（Element）

Parts of a block and have no standalone meaning. Any element is semantically tied to its block.

元素是块的组成部分，没有独立的意义，并且在语义上与它对应的块关联。

##### 命名（Naming）

Element names may consist of Latin letters, digits, dashes and underscores. CSS class is formed as block name plus two underscores plus element name: `.block__elem`

元素名称可以由拉丁字母，数字，中横线和下划线组成。CSS类可以在块名称后加上两个下划线再加上元素名称：`.block__elem`

##### HTML

Any DOM node within a block can be an element. Within a given block, all elements are semantically equal.

块中的任何DOM节点都可以看做一个元素。在一个块中的所有的元素在语义上相等。

```html
<div class="block">
    ...
    <span class="block__elem"></span>
</div>
```

##### CSS

* Use class name selector only
* No tag name or ids
* No dependency on other blocks/elements on a page


* 仅使用类选择器
* 不包含标签名称或ID
* 不依赖页面上的其他块/元素

**好的范例（Good）**

```css
.block__elem { color: #042; }
```

**不好的范例（Bad）**

```css
.block .block__elem { color: #042; }
    div.block__elem { color: #042; }
```

### 修饰符（Modifier）

Flags on blocks or elements. Use them to change appearance, behavior or state.

块或元素的标记。可以使用它们来改变块或元素的样式、行为或状态。


##### 命名（Naming）

Modifier names may consist of Latin letters, digits, dashes and underscores. CSS class is formed as block’s or element’s name plus two dashes: `.block--mod` or `.block__elem--mod`and `.block--color-black`with `.block--color-red`. Spaces in complicated modifiers are replaced by dash.


修饰符的名称可以由拉丁字母，数字，中横线和下划线组成。CSS类可以由块或元素的名称加上两个中横线组成：`.block--mod`或`.block__elem --mod`和 `.block--color-black`与`.block--color--red`。复杂修饰符中的空格被短划线所取代。

##### HTML

Modifier is an extra class name which you add to a block/element DOM node. Add modifier classes only to blocks/elements they modify, and keep the original class:

修饰符是添加到块/元素DOM节点的额外类的名称。我们只将修饰符类添加到修改过的块/元素，并保留它们原始的类：

**好的范例（Good）**
```html
<div class="block block--mod">...</div>
    <div class="block block--size-big block--shadow-yes">...</div>
```

**不好的范例（Bad）**

```html
<div class="block--mod">...</div>
```

##### CSS

Use modifier class name as selector:

使用修饰符的类名作为选择器：

```css
.block--hidden { }
```
To alter elements based on a block-level modifier:

若要基于块级修改器来更改元素，请执行以下操作：

```css
.block--mod .block__elem { }
```
Element modifier:

元素修饰符：

```css
.block__elem--mod { }
```

### 范例（Example）

Suppose you have block form with modifiers `theme: "xmas"` and `simple: true` and with elements `input` and `submit`, and element `submit` with its own modifier `disabled: true`for not submitting form while it is not filled:

在此，假设您有以下修饰符的块：`theme: "xmas"` 和 `simple: true`，并且有元素`input` 和 `submit`，同时元素`submit`有本身为那些在没有填充时不显示的修饰符`disabled：true`时代码如下：

##### HTML
```html
<form class="form form--theme-xmas form--simple">
    <input class="form__input" type="text" />
    <input class="form__submit form__submit--disabled" type="submit" />
</form>
```

##### CSS
```css
.form { }
.form--theme-xmas { }
.form--simple { }
.form__input { }
.form__submit { }
.form__submit--disabled { }
```
