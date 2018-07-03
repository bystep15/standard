title: 00、模块化CSS理论——BEM目录
categories: [理论, css, bem]
date: 2018/06/28 19:30:00
tags: [理论, css, bem]
---

[BEM](http://getbem.com)（Block Element Modifier），块元素修饰符，在SMACSS的基础上修改toggle组件的示例如下：

```html
<div class="toggle toggle—simple”>
    <div class=“toggle__control toggle__control—-active”>
        <h1 class=“toggle__title”>Title 1</h1>
    </div>
    <div class=“toggle__details toggle__details--active“>…</div>
    ...
</div>
```

BEM只是一个CSS类名命名规则，让每一个CSS类名具备详细的自描述性，不涉及如何书写CSS结构，只是建议每个元素都添加带有如下内容的CSS类名：

1. 块名：所属组件的名称。
2. 元素：元素在块里面的名称。
3. 修饰符：任何与块或元素相关联的修饰符。

元素名加在双下划线之后（例如`toggle__details`），修饰符加在双横杠之后（如`toggle__details—-active`）。

## 资料翻译列表

1. [介绍（Introduction）](/standard/2018/06/28/01、介绍（introduction）.html)
2. [命名（Naming）](/standard/2018/06/28/02、命名（naming）.html)
3. [常见问题（FAQ）](/standard/2018/06/28/03、常见问题（faq）.html)
