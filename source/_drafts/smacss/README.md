# 模块化CSS理论——SMACSS

[SMACSS](https://smacss.com)（Scalable and Modular Architecture for CSS），模块化的可扩展CSS，toggle组件的示例如下：

```html
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

- [1.关于作者（About the Author）](01-About-the-Author.md)
- [2.介绍（Introduction）](02-Introduction.md)
- [3.对CSS的规则进行分类（Categorizing CSS Rules）](03-Categorizing-CSS-Rules.md)
- [4.基本规范（Base Rules）](04-Base-Rules.md)
- [5.布局规范（Layout Rules）](05-Layout-Rules.md)
- [6.模块规范（Module Rules）](06-Module-Rules.md)
- [7.状态规范（State Rules）](07-State-Rules.md)
- [8.主题规范（Theme Rules）](08-Theme-Rules.md)
- [9.状态改变（Changing State）](09-Changing-State.md)
- [10.适用性的深度（Depth of Applicability）](10-Depth-of-Applicability.md)
- [11.选择器性能（elector Performance）](11-Selector-Performance.md)
- [12.HTML5和SMACSS（HTML5 and SMACSS）](12-HTML5-and-SMACSS.md)
- [13.原型（Prototyping）](13-Prototyping.md)
- [14.预处理器（Preprocessors）](14-Preprocessors.md)
- [15.从基本规则中分离（Drop the Base）](15-Drop-the-Base.md)
- [16.图标模块（The Icon Module）](16-The-Icon-Module.md)
- [17.复杂的继承（Complicated Inheritance）](17-Complicated-Inheritance.md)
- [18.Screencast：应用原则（Screencast: Applying the Principles）](18-Screencast-Applying-the-Principles.md)
- [19.Screencast:避免内容特定的上下文（Screencast: Avoiding Content-specific Context）](19-Screencast-Avoiding-Content-specific-Context.md)
- [20.格式化代码（Formatting Code）](20-Formatting-Code.md)
- [21.源文件（Resources）](21-Resources.md)
