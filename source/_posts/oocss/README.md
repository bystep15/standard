title: 00、模块化CSS理论——OOCSS目录
categories: [理论, css, oocss]
date: 2017/12/31 09:30:00
tags: [理论, css, oocss]
---

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
2. 分离容器和内容：指的是不再将元素位置作为样式的限定词，如上例中`toggle`、`toggle-control`、`toggle-title`和`toggle-detail`4个类。


## 资料翻译列表
1. [面向对象的CSS（Object Oriented CSS）](/standard/2018/01/02/01、面向对象的css（object-oriented-css）.html)
2. [模板（Template）](/standard/2018/05/29/02、模板（template）.html)
3. [网格（grids）](/standard/2018/06/06/03、网格（grids）.html)
4. [标准模块格式（Standard Module Format）](/standard/2018/06/06/04、标准模块格式（standard-module-format）.html)
5. [模块（Modules）](/standard/2018/06/26/05、模块-容器对象（modules-container-objects）.html)
6. [模块的表现形式（Module Skins）](/standard/2018/06/26/06、模块皮肤（module-skins）.html)
7. [内容（Content）](/standard/2018/06/27/07、内容（content）.html)
8. [按钮（Buttons）](/standard/2018/06/27/08、按钮（buttons）.html)
9. [谈话框（Talk Bubbles）](/standard/2018/06/27/09、对话框（talk-bubbles）.html)
10. [滚动栏（Carousel）](/standard/2018/06/28/10、走马灯（carousel）.html)
11. [UML](/standard/2018/06/28/11、uml.html)
12. [分级浏览器支持（Graded Browser Support）](/standard/2018/06/28/12、浏览器分级支持（graded-browser-support）.html)
13. [常见问题（FAQ）](/standard/2018/06/28/13、常见问题（faq）.html)
