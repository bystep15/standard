# 模块化CSS理论——OOCSS

[OOCSS](http://oocss.org)（Object-Oriented CSS，[Github](https://github.com/stubbornella/oocss/wiki)、[FAQ](https://github.com/stubbornella/oocss/wiki/faq)），面向对象的CSS，典型案例是BootStrap，toggle组件的示例如下：

```html
<div class="toggle simple">
    <div class="toggle-control open">
        <h1 class="toggle-title">Title 1</h1>
    </div>
    <div class="toggle-details open">...</div>
    ...
</div>
```

主要原则有以下两个：

1. 分离结构和外观：意味着将视觉特性定义为可复用的单元，如上例中`toggle`、`toggle-control`、`toggle-title`和`toggle-detail`4个类是结构类，simple是外观类。
2. 分离容器和内容：指的是不再将元素位置作为样式的限定词，如上例中`toggle`、`toggle-control`、`toggle-title`和`toggle-detail`4个类只是。

## 资料翻译列表


- [1.面向对象的CSS（Object Oriented CSS）](01-Object-Oriented-CSS.md)
- [2.模板（Template）](02-Template.md)
- [3.网格（grids）](03-Grids.md)
- [4.标准模块格式（Standard Module Format）](04-Standard-Module-Format.md)
- [5.模块（Modules）](05-Module.md)
- [6.模块的表现形式（Module Skins）](06-Module-Skins.md)
- [7.内容（Content）](07-Content.md)
- [8.按钮（Buttons）](08-Buttons.md)
- [9.谈话框（Talk Bubbles）](09-Talk-Bubbles.md)
- [10.滚动栏（Carousel）](10-Carousel.md)
- [11.UML](11-UML.md)
- [12.分级浏览器支持（Graded Browser Support）](12-Graded-Browser-Support.md)
- [13.常见问题（FAQ）](13-FAQ.md)
