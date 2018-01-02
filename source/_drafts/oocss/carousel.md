# Carousel 滚动栏

Documenting how this should work.

使用文档

* 100% of the width of its parent container, adapts to any sized container.
* Controls can be above, below, or right/left.
* Items width must be set in pixels (they can’t be %, no way to inherit container width from parent’s parent)
* Ideally it would not have half-items visible, in JS remove the extra bit or expand the units to fill more space?

* 按照其父容器的100％的宽度，适应于任何尺寸的容器。
* 控制组件可以在上方，下方或右侧/左侧。
* 元素宽度必须以像素为单位（它们不能为％，无法从父级的父级容器继承宽度）
* 理想情况下，它不会有半块可见，可以在JS中删除额外的区域或扩大比例以填补更多的空间

Brainstorming common markup for tabs, carousel, toggle, and accordion using the html5 syntax.

使用html5语法来设计标签，滚动栏，切换块和手风琴的通用标签。

## tabs 标签页

```html
<div class="section tabs">
  <div class="control">
    <ul> <!-- menu? -->
      <li>Tab 1</li>
      <li>Tab 2</li>
      <li>Tab 3</li>
    </ul>
  </div>
  <div class="details open"> Content Area </div>
  <div class="details"> Content Area </div>
  <div class="details"> Content Area </div>
</div>
```

## toggle block 切换块

```html
<div class="section toggle">
  <div class="control">
    <h1>Clicking on me toggles the display of the content area</h1>
  </div>
  <div class="details open"> Content Area </div>
</div>
```


## Carousel 滚动栏

```html
<div class="section carousel">
  <div class="control"> radio buttons for section and buttons for left/right or top/bottom scroll </div>
  <div class="details open"> Content Area </div>
</div>
```


## Accordion 手风琴

```html
<div class="section accordion">
  <div class="section">
    <div class="control">
      <h1>Clicking on me opens the adjacent accordion content area</h1>
    </div>
    <div class="details open"> Content Area </div>
  </div>
  <div class="section">
    <div class="control">
      <h1>Clicking on me opens the adjacent accordian content area</h1>
    </div>
    <div class="details"> Content Area </div>
  </div>
  <div class="section">
    <div class="control">
      <h1>Clicking on me opens the adjacent accordian content area</h1>
    </div>
    <div class="details"> Content Area </div>
  </div>
</div>
```

