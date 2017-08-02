# 模块化CSS理论——SMACSS

[SMACSS](https://smacss.com)（Scalable and Modular Architecture for CSS），模块化的可扩展CSS，toggle组件的示例如下：

```
<div class="toggle toggle-simple”>
<div class="toggle-control is-active">
<h1 class="toggle-title">Title 1</h1>
</div>
<div class="toggle-details is-active“>...</div>
...
</div>
```

把样式系统划分为5个类别：

1. 基础：整个页面纯标记（所有标签都不添加CSS）显示的基本外观样式。
2. 布局：把页面分成不同区域。
3. 模块：设计中的模块化、可复用的单元。
4. 状态：描述在特定的状态或情况下，模块或布局的显示方式。
5. 主题：一个可选的视觉外观层，可以为页面更换不同主题。

对于如何创建功能的小模块，SMACSS和OOCSS有许多相似之处。都是把样式作用域限定到根节点的CSS类名上，然后通过皮肤（OOCSS，simple是皮肤）或子模块（SMACSS，`toggle-simple`是toggle组件的一个子模块）进行修改。

## 资料翻译列表
