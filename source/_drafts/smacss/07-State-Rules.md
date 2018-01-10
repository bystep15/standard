# 状态规范（State Rules）

[原文](https://smacss.com/book/type-state)

A state is something that augments and overrides all other styles. For example, an accordion section may be in a collapsed or expanded state. A message may be in a success or error state.

状态是用来扩展和覆盖所有其他样式的情况。 例如，可折叠菜单部分可能处于折叠状态或展开的状态。 消息可能处于成功或错误的状态。

States are generally applied to the same element as a layout rule or applied to the same element as a base module class.

状态通常应用在类似于布局规则的元素上，或应用在与基本模块类相同的元素上。

状态应用在一个元素上（State applied to an element）

```
<div id="header" class="is-collapsed">
    <form>
        <div class="msg is-error">
            There is an error!
        </div>
        <label for="searchbox" class="is-hidden">Search</label>
        <input type="search" id="searchbox">
    </form>
</div>

```


The header element just has an ID. As such we can assume that any styles, if there are any, on this element are for layout purposes and that the `is-collapsed` represents a collapsed state. One might presume that without this state rule, the default is an expanded state.

header元素只有一个ID。因此，如果有的话，我们可以假设任何应用在一个元素上的样式是出于布局的考虑，也就是说`is-collapsed`表示折叠的状态。 有人可能会认为，没有这个状态规范，默认的情况是一个扩展的状态。

The `msg` module is simple enough and has an error state applied to it. One could imagine a success state could be applied to the message, alternatively.

`msg`模块足够简单，并且它表示一个错误的状态。相对应的，我们可以认为一个成功的状态也可以应用在这个信息上。

Finally, the field label has a hidden state applied to hide it from sight but still keep it for screen readers. In this case, we are actually applying the state to a base element and not overriding a layout or module.

最后，label标签有一个隐藏的状态来表示对用户隐藏，但屏幕阅读器仍然可以捕获它。 在这种情况下，我们实际上对基本元素应用这个状态，而不是对布局或模块进行覆盖。

### 它不是仅仅是个模块么？（Isnʼt it just a module?）

There is plenty of similarity between a sub-module style and a state style. They both modify the existing look of an element. However, they differ in two key ways:

1. State styles can apply to layout and/or module styles; and
2. State styles indicate a JavaScript dependency.

在子模块样式和状态样式之间有很多相似之处。 它们都可以修改元素的现有外观。 但是，它们在以下两个关键的地方有所不同：

1. 状态样式可以被应用到布局和（或者）模块样式上；
2. 状态样式可以用来表明一个JavaScript依赖。

It is this second point that is the most important distinction. Sub-module styles are applied to an element at render time and then are never changed again. State styles, however, are applied to elements to indicate a change in state while the page is still running on the client machine.

第二点是最主要的区别。子模块样式是在一个模块渲染的时候被应用到元素上的，并且永远都不会改变。而状态样式不同，在页面仍在客户端进行运行时，它也可以在元素状态发生改变时被应用到元素上。

For example, clicking on a tab will activate that tab. Therefore, an `is-active` or `is-tab-active` class is appropriate. Clicking on a dialog close button will hide the dialog. Therefore, an `is-hidden` class is appropriate.

例如，点击一个标签将会激活这个标签。因此，一个`is-active`的或`is-tab-active`类是合适的。 点击对话框关闭按钮将会隐藏对话框。 因此，一个`is-hidden`类是合适的。

## 使用！important（Using !important）

States should be made to stand alone and are usually built of a single class selector.

状态通常都应当独立表示，并且有一个单一的类选择器构成。

Since the state will likely need to override the style of a more complex rule set, the use of `!important` is allowed and, dare I say, recommended. (I used to say that `!important` was never needed but on complex systems, it is often a necessity.) You won’t normally have two states applied to the same module or two states that tend to affect the same set of styles, so specificity conflicts from using `!important` should be few and far between.

由于状态很可能需要重写更复杂的规范的样式，所以使用`!important`是可行的，换句话说，我在此推荐使用。（我曾经说过，`!important`从不需要被使用到，但是在复杂的结构中，这往往是必须的）。通常情况下，您在相同的模块上不会有两个状态，或者两个状态往往会影响同一组样式。 从使用`!important`带来的问题应该是少之又少的。

With that said, be cautious. Leave `!important` off until you actually and truly need it (and you will see why in this next example). Remember, the use of `!important` should be avoided for all other rule types. Only states should have it.

谨慎点说。 直到您真正需要使用`!important`时再使用（在这个下一个例子您就知道为什么了）。请记住，所有其他规则类型都应该避免使用`!important`，只有状态才可以使用它。

## 将模块与状态规则相结合（Combining State Rules with Modules）

Inevitably, a state rule will not be able to rely on inheritance to apply its style in the right place. Sometimes a state is very specific to a particular module where styling is very unique.

不可避免的是，一个状态规则是不允许通过依赖继承将样式应用到正确的位置上。 有时候一个状态对于一个样式是独一无二的模块来说非常独特的。

In a case where a state rule is made for a specific module, the state class name should include the module name in it. The state rule should also reside with the module rules and not with the rest of the global state rules.

在对特定模块应用状态规范时，状态类的名称中应包含模块的名称。状态规范也应该遵守模块规范，而不是遵循其他的全局状态规范。

对于模块的状态规范（State rules for modules）

```
.tab {
    background-color: purple;
    color: white;
}

.is-tab-active {
    background-color: white;
    color: black;
}
```

If you are doing just-in-time loading of your CSS, generic states should be considered part of the base and global styles and loaded on initial page load. The styles for a particular module wonʼt need to be loaded until that particular module is loaded.

如果您正在对CSS进行即时加载，则通用状态应被考虑为基本和全局样式的一部分，并在初始页面加载时开始加载。特定模块的样式在该特定模块被加载前都不应当被加载。
