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
