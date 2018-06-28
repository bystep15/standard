title: 10、走马灯（Carousel）
categories: [理论, css, oocss]
tags: [理论, css, oocss]
date: 2018/06/28 09:30:00
---

[原文](https://github.com/stubbornella/oocss/wiki/Carousel-)

Documenting how this should work.

- 100% of the width of its parent container, adapts to any sized container.
- Controls can be above, below, or right/left.
- Items width must be set in pixels (they can't be %, no way to inherit container width from parent's parent)
- Ideally it would not have half-items visible, in JS remove the extra bit or expand the units to fill more space?

使用文档

- 宽度属性为其父容器的100％，适应于任何尺寸的容器。
- 控制组件可以在上方，下方或右侧/左侧。
- 元素宽度必须以像素为单位（不能设为百分比，无法从父级的父级容器继承宽度）
- 理想情况下，不会显示半个元素，使用JS删除多余的空间或者填充更多的空间也许是个方法？

Brainstorming common markup for tabs, carousel, toggle, and accordion using the html5 syntax.

使用html5语法来设计标签页，走马灯，切换块和手风琴的通用标签。

## 标签页（tabs）
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

## 走马灯（Carousel）
```html
<div class="section carousel">
    <div class="control"> radio buttons for section and buttons for left/right or top/bottom scroll </div>
    <div class="details open"> Content Area </div>
</div>
```

## 切换块（toggle block）
```html
<div class="section toggle">
    <div class="control">
        <h1>Clicking on me toggles the display of the content area</h1>
    </div>
    <div class="details open"> Content Area </div>
</div>
```

## 手风琴（Accordion）
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
