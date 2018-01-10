# 模块规范（Module Rules）

[原文](https://smacss.com/book/type-module)

As briefly mentioned in the previous section, a Module is a more discrete component of the page. It is your navigation bars and your carousels and your dialogs and your widgets and so on. This is the meat of the page. Modules sit inside Layout components. Modules can sometimes sit within other Modules, too. Each Module should be designed to exist as a standalone component. In doing so, the page will be more flexible. If done right, Modules can easily be moved to different parts of the layout without breaking.

正如前一节提到的那样，模块是页面的一个更加独立的组件。 它可能是您的导航栏，您的滚动栏，你的对话框或是其他的小部件等等。 这是页面的内容部分。 模块通常位于布局组件之中。 有时也可能位于其他模块中。 每个模块都应当被设计为独立的组件。因为这样做可以使页面会更加灵活。 如果操作得当，模块可以轻松地移动到布局的不同部分而不会有其他影响。

When defining the rule set for a module, avoid using IDs and element selectors, sticking only to class names. A module will likely contain a number of elements and there is likely to be a desire to use descendent or child selectors to target those elements.

当为模块定义规范时，我们要避免使用ID选择器和元素选择器，只能使用类来命名。一个模块可能包含许多元素，而且很可能会使用后代或子类选择器来定位这些元素。

模块范例（Module example）

```
.module > h2 {
    padding: 5px;
}

.module span {
    padding: 5px;
}
```

## 避免使用元素选择器（Avoid element selectors）

Use child or descendant selectors with element selectors if the element selectors will and can be predictable. Using `.module span` is great if a span will predictably be used and styled the same way every time while within that module.

如果元素的选择器是可以确定的，我们通常会对元素使用子类或者后代选择器。如何一个span是可预期的，那么在模块中使用`.module span`比其他的方法都要好。

通用元素的样式（Styling with generic element）

```
<div class="fld">
    <span>Folder Name</span>
</div>

/* The Folder Module */
.fld > span {
    padding-left: 20px;
    background: url(icon.png);
}

```

The problem is that as a project grows in complexity, the more likely that you will need to expand a component’s functionality and the more limited you will be in having used such a generic element within your rule.

随着项目变得复杂，问题也随着而来，随着对于组件功能性的要求更强，您在规则中使用通用元素的可能性也就越大。

通用元素的样式（Styling with generic element）

```
<div class="fld">
    <span>Folder Name</span> 
    <span>(32 items)</span>
</div>

```

Now we are in a pickle. We don’t want the icon to appear on both elements within our folder module. Which leads me to my next point:

现在我们考虑这样一个情况。 我们不希望图标出现在我们的容器模块中的所有元素上。为此我提出以下内容：

只包含一个包含语义的选择器。 跨度或div没有。 一个标题有一些。 在元素上定义的类有很多。

使用通用元素的样式

Only include a selector that includes semantics. A span or div holds none. A heading has some. A class defined on an element has plenty.

只包含一个具有语义化的选择器；没有span或者div；可以有一些标题；在一个元素上可以有多个类。

通用元素的样式（Styling with generic element）

```
<div class="fld">
    <span class="fld-name">Folder Name</span> 
    <span class="fld-items">(32 items)</span>
</div>

```

By adding the classes to the elements, we have increased the semantics of what those elements mean and removed any ambiguity when it comes to styling them.

通过给元素添加类属性，我们通过语义化的方式来介绍元素的功能，并消除了样式的不明确性。

If you do wish to use an element selector, it should be within one level of a class selector. In other words, you should be in a situation to use child selectors. Alternatively, you should be extremely confident that the element in question will not be confused with another element. The more semantically generic the HTML element (like a span or div), the more likely it will create a conflict down the road. Elements with greater semantics like headings are more likely to appear by themselves within a container and you are more likely able to use an element selector successfully.

如果您确实希望使用元素选择器，那它应当和类选择器位于同一个级别。 换句话说，你应当位于使用子类选择器的情况下使用元素选择器。 或者，您应该非常明确，所涉及的元素不会与其他元素混淆。 使用的HTML元素（比如span或者div）在语义上越通用，它就越有可能在渲染时产生冲突。具有更强语义性的元素（比如标题）更有可能在容器中出现，而且更有可能使用元素选择器。

## 新的上下文（New Contexts）

Using the module approach also allows us to better understand where context changes are likely to occur. The need for a new positioning context, for example, is likely to happen at either the layout level or at the root of a module.

使用模块方法还可以让我们更好地理解结构上可能发生变化的地方。 例如，对新的定位上下文的需求可能位于在布局级别的部分或者模块的根部。

## 子类模块（Subclassing Modules）

When we have the same module in different sections, the first instinct is to use a parent element to style that module differently.

当我们在不同的部分中有相同的模块时，首要的任务是使用父元素对该模块渲染不同的样式。

子类（Subclassing）

```
.pod { 
    width: 100%; 
}
.pod input[type=text] { 
    width: 50%; 
}
#sidebar .pod input[type=text] { 
    width: 100%; 
}

```

The problem with this approach is that you can run into specificity issues that require adding even more selectors to battle against it or to quickly fall back to using `!important`.

这种方法的问题就是，当遇到特殊情况的时候，您需要添加更多的选择器来进行实现修改，或者使用`!important`来覆盖。

Expanding on our example pod, we have an input with two different widths. Throughout the site, the input has a label beside it and therefore the field should only be half the width. In the sidebar, however, the field would be too small so we increase it to 100% and have the label on top. All looks well and good. Now, we need to add a new component to our page. It uses most of the same styling as a `.pod`and so we re-use that class. However, this pod is special and has a constrained width no matter where it is on the site. It is a little different, though, and needs a width of 180px.

通过扩展我们以上pod的例子，我们有两个不同宽度的输入。 在整个网站中，输入框旁边有一个标签，因此该部分应该只有一半的宽度。 然而，在侧边栏的部分上，该部分的宽度太小了，所以我们需要将其增加到100％的宽度，并将标签置于其上方。 一切看起来都不错。 现在，我们需要在我们的页面中添加一个新的组件。 它使用的样式和`.pod`大体相同，所以我们重新使用这个类。 但是，这个pod比较特殊的是无论在页面上什么位置，它都有一个限制的宽度。 虽然会有些许不同，但它还是需要180px的宽度。

覆盖特殊性（Battling against specificity）

```
.pod { 
    width: 100%; 
} 
.pod input[type=text] { 
    width: 50%; 
}
#sidebar .pod input[type=text] { 
    width: 100%; 
}

.pod-callout { 
    width: 200px; 
}
#sidebar .pod-callout input[type=text],
.pod-callout input[type=text] { 
    width: 180px; 
}

```

We are doubling up on our selectors to be able to override the specificity of `#sidebar`.

我们正在增加我们的选择器，以便能够覆盖`#sidebar`的特殊性。

What we should do instead is recognize that the constrained layout in the sidebar is a subclass of the pod and style it accordingly.

我们应该做的是意识到侧边栏中的约束布局是pod的一个子类，并据此进行设计。

覆盖特殊性（Battling against specificity）

```
.pod { 
    width: 100%; 
} 
.pod input[type=text] { 
    width: 50%; 
}
.pod-constrained input[type=text] { 
    width: 100%; 
}

.pod-callout { 
    width: 200px; 
}
.pod-callout input[type=text] { 
    width: 180px; 
}

```

With sub-classing the module, both the base module and the sub-module class names get applied to the HTML element.

通过对模块进行子分类，基本模块和子模块类名都被应用到HTML元素中。

HTML中子模块的类命名（Sub-module class name in HTML）

```
 <div class="pod pod-constrained">...</div>
<div class="pod pod-callout">...</div> 
```

Try to avoid conditional styling based on location. If you are changing the look of a module for usage elsewhere on the page or site, sub-class the module instead.

尽量避免基于位置的条件样式。如果要改变模块的外观以在页面或站点的其他位置上使用，请对子模块进行修改。

To help battle against specificity (and if IE6 isn’t a concern), then you can double up on your class names like in the next example.

为了帮助覆盖掉特殊性（在此不考虑IE6），那么你可以像下一个例子那样添加更多的类名。

子类（Subclassing）

```
.pod.pod-callout { }

<!-- In the HTML -->
<div class="pod pod-callout"> ... </div>

```


You may be concerned about this, depending on the order of loading. For example, on Yahoo! Mail, we have code coming from different places. We had our base button styles and then we had a special set of buttons for the compose screen. However, when you clicked to add a contact to your address book, it loaded a component from a different product: Address Book. (Yes, the address book is a different product within Yahoo!.) The address book loaded its own base button styles, thereby overwriting the sub-classed button styles that we had.

您可能会担心这一点，这里的样式取决于加载的顺序。 例如，在Yahoo! 邮件中，我们有来自不同地方的代码。 我们有我们的基本按钮样式，然后我们对于不同的屏幕有一系列特殊的按钮集合。但是，当您通过点击将将联系人添加到通讯簿时，它将从不同的产品中加载通讯簿组件。（是的，地址簿与Yahoo！不是一个产品）。地址簿加载了自己的基本按钮样式，从而覆盖了我们拥有的子类按钮样式。

If load order is a factor in your project, watch out for specificity issues.

如果加载顺序是您的项目中的一个要素，请注意特殊性的问题。

While more specific layout components assigned with IDs could be used to provide specialized styling for modules, sub-classing the module will allow the module to be moved to other sections of the site more easily and you will avoid increasing the specificity unnecessarily.

尽管可以使用ID选择器来为更特殊的布局组件提供专门的模块样式，但模块的子类允许模块更容易地移动到网站的其他部分，并且避免增加不必要的特殊性。

