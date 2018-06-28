title: 03、常见问题（FAQ）
categories: [理论, css, bem]
date: 2018/06/28 22:30:00
tags: [理论, css, bem]
---

[原文](http://getbem.com/faq/)

These Frequently Asked Question are real questions of developers started with BEM, answered by the GetBEM community. Feel free to [ask your question](https://github.com/getbem/getbem.com/issues/new?title=FAQ:%20Type%20your%20question%20here) too, and we will answer it as well.

这些常见问题是刚刚开始使用BEM的开发人员常遇到的问题，由GetBEM社区回答。您可以在社区里面[随意问问题](https://github.com/getbem/getbem.com/issues/new?title=FAQ:%20Type%20your%20question%20here)，我们会在上面回答。

- [为什么我要选择BEM而不是其他的CSS模块？（Why should I choose BEM and not another CSS modular solution?）](#why-bem)
- [为什么修饰符的CSS类不能被认作为组合选择器？（Why are the modifier CSS classes not represented as a combined selector?）](#why-the-modifier-classes-are-prefixed)
- [为什么我需要为块元素提供CSS类而不是使用语义化的自定义标签？（Why do I need CSS classes for block instead of using semantic custom tags?）](#custom-tags-for-blocks)
- [为什么我需要为一个带修饰符的块元素提供块和修饰符前缀的类？（Why do I need to combine block and prefixed modifier class for a modified block?）](#block-modifier-mix)
- [一个块修饰符会影响到元素么？（Can a block modifier affect elements?）](#block-modifier-affects-elements)
- [我可以创建一个可以被任何块使用的全局修饰符么？（Can I create a global modifier applicable to any block?）](#can-i-create-global-modifier)
- [我可以在选择器上结合一个标签和类么，就像button.button？（Can I combine a tag and a class in selector like button.button?）](#encapsulating-tag-selector)
- [将修饰符命名为它们在CSS中的样式的行为好么？就像`.block__element--border-bottom-5px`一样。（Is this good to name modifiers corresponding to what they have in CSS? Like `.block__element--border-bottom-5px`.）](#css-modifier-names)
- [一个在另一个元素中的元素的类名应该怎么设置？像`.block__el1__el2`这样么？（What would be a class name for an element inside another element? `.block__el1__el2`?）](#css-nested-elements)
- [我听说BEM不推荐使用全局CSSreset，为什么？（I've heard that BEM does not recommend global CSS resets? Why?）](#global-css-resets)
- [没找到答案？（Did not find the answer?）](#ask-your-question)


<a id="#why-bem"></a>
## 为什么要我选择BEM作为CSS的模块？（Why should I choose BEM as a modular solution for CSS?）

> There are some other modular solutions for CSS (such as OOCSS, AMCSS, SMACSS, SUITCSS). What are the reasons to choose BEM?

> 现在有许多其他的CSS模块的解决方法（例如OOCSS，AMCSS，SMACSS和SUITCSS）。那为什么要选择BEM呢？

BEM provides solutions for all the frontend technologies: CSS, JavaScript, templating; and also for building process of your web application. The methodology is applicable anywhere. However, to apply this in JavaScript and templating you would need special frameworks whereas in CSS you may just follow the methodological recommendations. The CSS part of BEM is the easiest to take into your development process. This is why many use only it. On the other hand, if lately you would found your project fully BEMed (in CSS) and yourself happy for its grown maintenance, you probably would take next step in modularizing your web application. BEM CSS will be easier to coordinate with modular JavaScript and blocks-based project file structure.

BEM为所有的前端技术提供了解决方案：CSS，JavaScript，模板; 也可以用于构建您的Web应用程序。这种方法适用于任何地方。但是，要在JavaScript和模板中应用BEM，您需要特殊的框架，而在CSS中，您按照建议的方法去做就行。BEM的CSS部分是最容易引入到您的开发流程中的。这就是为什么许多人只使用它的原因。另一方面，如果最近您会发现您的项目完全通过BEMed实现了（在CSS中），并且您可以自己开始维护，那您可以利用模块化来完成您的Web应用程序的下一步。BEM CSS与模块化的JavaScript和基于块的项目文件结构结合使用可以让工作变得更轻松。

If speaking about CSS modular solutions only, the key feature of BEM is block's independence. Following the CSS recommendations enables to put a block into any place on a page and be sure that is won't be affected by its surroundings. Also, if you would lately need to nest another block into the current one, their full compatibility is guaranteed. In other words, when maintaining your web application you would be able to move blocks across the page, add others and combine them.

如果仅仅谈到CSS模块化的解决方案，BEM的关键特征就是块元素的独立性。根据BEM的CSS的建议，我们可以在网页上的任何位置放置一个块，并确保不会受到周围环境的影响。而且，如果您最近需要将另一个块嵌套到当前块中，原块的兼容性将会得到保证。换句话说，在维护Web应用程序时，您可以在整个页面上移动块元素，添加其他组件并将其组合起来。

BEM CSS unambiguously defines which CSS belongs to a piece of interface and so using it gives answers to questions "Can I remove this piece of code?" and "What happens and which interface parts will be affected if I change this piece of code?".

BEM CSS明确定义了哪些CSS属于一个界面，因此使用它可以解决“我可以删除这段代码吗？” 和“如果我更改了这段代码，会发生什么事情？哪些接口部件会受到影响？”的问题。

<a id="#why-the-modifier-classes-are-prefixed"></a>
## 为什么修饰符的CSS类不能被认作为组合选择器？(Why the modifier CSS classes are not represented as a combined selector?)

> BEM recommends to modify blocks like this `<div class="block block--mod">`. Why not to use the simple version like `<div class="block mod">`? Since we now have combined selectors `.block.mod`, it's easy to define all the CSS properties to it.

> BEM推荐像`<div class="block block--mod">`这样的修饰类。为什么不用简单的像`<div class="block mod">`这样的版本呢？因为我们结合了选择器`.block.mod`，通过它就就可以很容易地定义所有CSS属性。

The recommendation to prefix modifier CSS class with its block name has multiple reasons.

使用带块名称的修饰符的CSS类的前缀建议有多种原因。

Firstly, since it is possible to mix several blocks and elements at the same DOM node, we need to ensure that a modifier would affect only the block it belongs to. Let's say that we have a menu item element and a button mixed together. In HTML this construction is represented
by the following markup:

首先，通过它我们可以在同一个DOM节点上添加多个块和元素，所以我们需要确保修饰符只影响它所属的块元素。假设我们将一个菜单项的元素和一个按钮混合在一起。在HTML中，这种结构会是这样的：

```html
<div class="menu__item button"></div>
```

In this case adding `.active` modifier to them would affect both.

在这个例子中添加修饰符`.active`会对它们俩都产生影响。

```html
<div class="menu__item button active"></div>
```

All the 3 sit at the same DOM node, so it is impossible to differentiate if we mean `menu__item.active` or `button.active`. Whereas in the prefixed case the naming `button--active` unambiguously says as that this is only the button that has to be affected.

所有的3个类都在同一个DOM节点上，所以如果我们用`menu__item.active`或者`button.active`无法区分出它们。而在有前缀`button--active`的情况下 - 可以毫不含糊地说，当前元素是唯一会被影响的按钮。

Another point is CSS specificity. The combined selectors are more specific (means more important) than single class selectors. This means that you might have trouble when redefining them with parent block code.

另一点是CSS的特殊性。组合的选择器比单个选择器更具体（意味着更重要）。这意味着在用它们父节点块的代码重新定义它们时可能会遇到麻烦。

```html
<div class="header">
    <button class="button active">
</div>
```

If you already have `.button.active` selector in your code, the specificity of your redefining `.header .button` would be exactly the same as the specificity of modifier combined selector which makes you dependent on the order of the CSS rules declared. Whereas if you use a prefixed modifier, you can always be sure that the cascade selector `.header .button` will overwrite the `.button--active` modifier.

如果在您的代码中已经添加了`.button.active选择器，那么重定义`.header .button`的独特性与修饰符组合选择器的独特性完全相同，这使得最后的效果会依赖于您声明的CSS规则的顺序。而如果使用前缀修饰符，则始终可以确保级联选择器`.header .button`将覆盖`.button - active`修饰符的样式。

This makes life easier especially for maintainable projects.

这更有利于项目的可维护性。

The third point is that looking at the `<div class="block block--mod">` markup you can clearly see the block structure. It is easy to recognize that we have a block and its modifier and there is no different interpretations here. Unfortunately a grasp onto `<div class="block mod">` code does not give such information. Depending on what are the exact CSS classes sometimes it is impossible to recognize if we have a block and a modifier or a mix of 2 blocks here. This might be even more confusing if the names of the entities are complex or contracted/abbreviated (which sometimes happens in big projects).<br/> Clear understanding of a block structure is especially helpful when looking for corresponding code on a file system.

第三点是当您看看`<div class =“block block -mod”>`标记时，您可以清楚地看到块结构。我们很容易看到，此处我们有一个块元素和它的修饰符，这是确定的。不幸的是，使用`<div class =“block mod”>`代码并不能提供这样信息。如果依靠确切的CSS类，有时可能辨别不出我们是由一个块元素，还是一个修饰符或是2者的混合。 如果实体的名称是复杂的或是缩写的（这在大项目中有时会发生），情况可能会更加糟糕。

You will also appreciate `.block--mod` practice when refactoring and use global search over all your project files. Imagine the same looking for not-prefixed `.mod` and all the HTML pieces it might be in.

当重构和使用全局搜索您的所有项目文件时，您也许会喜欢使用`.block--mod`这样的方法。可以想象一下，如果`.mod`和其他HTML代码没有前缀，情况又是什么样的。

And lastly, from a development process standpoint the difference between `.block.mod` and `.block--mod` is only one symbol. Using `-` instead of `.` costs nothing but it brings all the benefits listed above. Moreover, since pre-processor began to support BEM notation, it is pretty natural to write `&--mod` there and finally get a modifier declared as it was recommended.

最后，从开发过程的角度来看，`.block.mod`和`.block--mod`之间的区别只是一个符号。 使用`-` 而不是`.` 不会花费任何东西，但它会带来上面列出的所有好处。而且，由于预处理器开始支持BEM的声明，所以在那里编写`＆--mod`是很自然的，最后，您会得到一个推荐的修饰符。

<a id="custom-tags-for-blocks"></a>
## 为什么我需要为块元素提供CSS类而不是使用语义化的自定义标签？(Why do I need CSS classes for block instead of using semantic custom tags?)

> Blocks can be represented as custom tags which we may define CSS rules for. Looks like we do not need CSS classes for blocks at all. They can be used for modifiers only, like `<button class="mod"/>`.

> 块是可以根据我们的CSS规则定义的自定义标签。所以看起来我们根本不需要CSS类的块。它们只能用于修饰符，如`<button class =“mod”/>`。

Using custom tags as block selectors is indeed one of the BEMish solutions and can be used. However this variant is less flexible than the recommended "class" approach.

使用自定义标签作为块选择器确实是BEMish的解决方案之一，我们也可以使用它。但是，这个变体与我们推荐的“class”方法相比不是那么灵活。

This is more likely that you would need to prefix modifier classes with their block name to provide them namespace. The details are uncovered in ["Why the modifier CSS classes are prefixed with their parent block name?"](#why-the-modifier-classes-are-prefixed) question. So, finally the custom-tag version of a block is like `<block class="block--mod"/>`. This does not look very different from `<div class="block block--mod">` especially assuming that being tag-independent you can use any custom node and stay with `<block class="block block--mod">`.

现在的情况是很可能需要您根据前缀修饰符类与它们的块名称来为它们提供命名空间。详细情况您可以在[“为什么修饰符CSS类以其父块名称为前缀？”](#why-the-modifier-classes-are-prefixed)中找到。所以，一个块的自定义标签最后很可能就像`<block class =“block-mod”/>`这样。假设现在标签是独立的，你可以使用任何自定义节点，并且在`<block class =“block block-mod”>`中，效果与`<div class =“block block-mod”>`看起来没有什么两样。

Second drawback is that "tag" version makes using the mixes of blocks impossible whereas the "class" version represent that naturally by `<div class="block1 block2">`.

第二个缺点是“标签”的版本使得混用块是不可能的，而“class”的版本自然地由`<div class =“block1 block2”>`表示。

And the last clench against such an approach is that in many cases you are not able to represent your blocks with custom tags at all. For a `link` block you definitely need `<a>` tag, and the same for `<input>`.

最后一个原因是在很多情况下，您不能用自定义标签来表示您的块。对于`link`块，您肯定需要`<a>`标签，对于`<input>`标签也是如此。

<a id="block-modifier-mix"></a>
## 为什么我需要为一个带修饰符的块元素提供块和修饰符前缀的类？(Why do I need to combine block and prefixed modifier class for a modified block?)

> Why does both block's and modifier's class sit together in the modified block like `<div class=”block block--mod”>`?

> Everything about a modified block can be described in `.block--mod`. If there is something common between 2 modifiers, it's possible to use preprocessor's mixins to avoid copy-paste.


> 为什么块和修饰符的类在修饰符的块中一起使用的效果像是`<div class =“block block - mod”>`？

> 关于修饰块的一切可以用`.block - mod`来描述。如果两个修饰符之间有共同之处，可以使用预处理器的mixin来避免重复。

This approach is possible thanks to preprocessors. However it brings some drawbacks which you should be aware of.

这种方法多亏了预处理器。但是它也会带来一些您能意识到的问题。

In the case of combining 2 or more modifiers at the same block `<div class="block--theme--christmas block--size--big">`, you would get the core block's styles twice. However this depends on the preprocessor algorithms.

如果在同一个块`<div class =“block - theme - christmas block - size - big”>`中使用了两个或更多个修饰符，您会生成两次块的样式。但这不是绝对的，这取决于您预处理器算法。

When adding/removing modifiers dynamically with JavaScript, the additional modifier is more handy. Switching it off would mean only removing one CSS class from the DOM node with no need to add the core block CSS class back as it sits there forever.

当用JavaScript动态添加或移除修饰符时，新添加上的修饰符更方便处理。不适用它意味着只需要从DOM节点中删除一个CSS类，而不需要添加CSS类，因为它就在那里不会改变。

<a id="block-modifier-affects-elements"></a>
## 一个块级修饰符会影响到元素么？（Can a block modifier affect elements?）

> If I have a block modifier, for example `xmas`, and I want the elements within that block to also be xmas themed, how would it be best to do it.

> Does a `--xmas` suffix for every element seem necessary? Or would this be the one use-case for nesting (e.g. `block--xmasblock__elem { ... }`?)

> 如果我有一个块级修饰符，就像`xmas`一样，并且我希望块中的元素也是xmas主题的，那么最好的方法是什么呢？

> 对每个元素来说，一个`--xmas`的后缀是否是必须的？或者这是嵌套的一个用例么？（例如`block-xmas block__elem {...}`？）

While in general BEM recommends avoiding nested selectors, in this case they are reasonable.

通常情况下，BEM建议不适用嵌套选择器，但是在这个案例中它们可以使用。

When creating the nested selector, you declare that one entity depends on another. Because BEM introduces independent components, such an approach is not suggested when we are speaking about 2 different blocks.

在创建嵌套选择器时，您声明一个实体依赖于另一个实体。因为BEM引入了独立的组件，所以当我们谈论2个不同的块元素时，并不建议这样的方法。

But when it comes to a block and its element, they are not of equivalent meaning. By definition, an element does not make any sense outside its parent block. So, an element is a block-dependent entity. Assuming this, it is quite normal and logical that an element is affected by the block's current state.

但是，当涉及到一个块和它的元素时，它们不具有同等的含义。 根据定义，一个元素若在其父块之外，它就没有任何意义。 所以，一个元素是一个块依赖的实体。基于这个假设，一个元素受到块当前状态的影响是很正常的，也是很合乎逻辑的。

So, this is a common pattern in BEM to code

所以，BEM的代码有一个统一的格式

```
.my-block--xmas .my-block__button {
	/* Jingle bells, jingle bells, jingle all the way.*/
}
```

<a id="can-i-create-global-modifier"></a>
## 我可以创建一个可以被任何块使用的全局修饰符么？（Can I create a global modifier applicable to any block?）

> I've heard that global modifiers like `visible`, `invisible`, `red`, `opacity50` are not welcomed in BEM. Why?

> I think it is useful to incorporate common properties like this in such a global class and then apply it to different blocks.


> 我曾听说过像`visible`, `invisible`, `red`, `opacity50`这样的全局修饰符在BEM中并不受欢迎。为什么呢？

> 我认为将上述这样的常见属性合并到全局类中，然后将其应用到不同的块中是有好处的的。

Indeed you can have 2 main CSS classes at the same DOM node. In BEM we call it `mix`:

确实，您在同一个DOM节点上可以有两个主要的CSS类，在BEM中我们称之为`mix`；

```html
<div class="block1 block2"></div>
```

But the important thing about it is that both `block1` and `block2` should be standalone blocks. This is slightly different from what people usually mean by "global modifiers", as modifiers do not have any sense on their own and are just a set of properties to change.

但是，重要的是`block1`和`block2`都应该是独立的块。这与人们通常所说的“全局修饰符”的含义略有不同，因为修饰符本身没有任何意义，它们只是表示一组需要改变的属性。

```html
<div class="block globalmod"></div>
```

If you think that in your case you would have a global modifier, these are the problems you may face:

如果您认为在您的项目中需要用到全局修饰符，那么您可能面对如下问题：

First of all the specificity problem appears. In a local modifier case CSS code goes like this:

首先是特殊性会出现问题。在使用本地修饰符的情况下，CSS代码如下所示：

```css
.block {
  display: block;
}
.block--hidden {
  display: none;
}
```

Both block and modifier selectors have the same specificity. As modifier declaration goes after the block, it redefines the CSS properties. These styles belong to block and are stored in the block file. Thus, independently on how the resultant CSS is built from source, you will always have them in this order and be sure that redefining happens.

块和修饰符选择器具有相同的特征。由于修饰符是在块声明之后声明的，所有它会重新定义CSS属性。属于块元素的样式会在块文件中存储。因此，不同于源代码生成的CSS的样式，如果您始终按照这个顺序生成代码，您就会得到新定义的CSS。

In the case of global modifier, its properties can be redefined by the blocks if they follow modifiers in code:

在全局修饰符的例子中，如果在代码中块元素CSS声明的位置在修饰符声明的后面的话，那么元素的属性会由块元素重新定义：

```css
.hidden { display: none }
/* ... */
.block { display: block }
```

```html
<div class="block hidden">you still see me</div>
```

One of the possible solutions to this problem is to raise the selector specificity of global modifiers by adding `!important` to them. But in this case any side-effects of such a global modifier might be overwritten only by declarations with the same `!important` instruction.

一个可以解决问题的方案是通过对它们增加`!important`来提高全局修饰符的选择器的特殊性。但是在这种情况下，全局修饰符只能被具有相同的`!important`的声明所覆盖。

Another way is to load global modifier CSS after all the other styles. But in this case you are not able any more to use lazy loading strategy for your components. The additional lazy CSS will still be loaded after the modifiers and you get the same problem.

另一种方法是在所有样式声明之后再加载全局修饰符。但是这种情况下不允许您的组件使用任何延迟加载。若您这样使用的话，延迟加载的CSS会覆盖最后声明的修饰符的样式，那您又会遇到相同的问题。

The next problem is combination of several global modifiers at the same block.

接下来的问题是如何在同一个块元素中结合几个全局修饰符。

```html
<div class="block mod1 mod2"></div>
```

In this case you absolutely have no control over the block. The order of modifiers in code can be different. If it conflicts with other declarations, changing the order can fix this conflict but lead to another one. The only way would be to redefine the mess in block. And don't forget about the `!important` to your hack.

因为代码中修饰符的顺序可能不同，所以您无法完全确定该块元素的样式。如果其中一个修饰符与其他的声明冲突，在改变顺序后，虽然可以解决这个冲突，但又导致其他的冲突。对于这个问题，唯一的办法是重新定义这些样式。记得不要忘记使用`!important`。

Also, depending on a block the same modifier can be implemented differently. Even the simple `.hidden` sometimes needs to be not `display: none` but `visibility: hidden` or even `position: absolute; left: -9999px` etc. And if you need to bring some changes into your block, it is much nicer not to waste time searching for all the places where this block can be combined with a global modifier. Especially assuming that such dependencies usually are not described anywhere.

而且，相同的修饰符在不同的块元素上可以有不同的样式。 即使是简单的`.hidden`有时不会选择`display: none`而是`visibility: hidden`，甚至是`position: absolute; left: -9999px`等等。如果想要在您的块元素中加入一些变化，您不用浪费时间去寻找整个块元素中所有可以和全局修饰符结合的地方。特别是这种依赖关系通常不会在任何的地方描述出来。

All this hell can be avoided by encapsulating a modifier in a block like `.block--mod`.

所有这一切都可以通过在一个像`.block--mod`这样的块中封装一个修饰符来避免。

Indeed using global modifiers makes the resultant code less. However if you measure the real difference in bytes it usually does not seem that big. Especially if you are using CSS optimizer which can combine selectors.

事实上，使用全局修饰符会使最后生成的代码量更少。但是，如果你用字节数来衡量实际的差异，那么差距通常看起来并不大。特别是如果您可以使用像CSS选择器这样的优化方式。

<a id="encapsulating-tag-selector"></a>
## 我可以在选择器上结合一个标签和类么，就像`button.button`？（Can I combine a tag and a class in selector like `button.button`?）

> I want to use selectors like `button.button` to encapsulate my blocks functionality within a particular tag. If lately someone else would use in their code `<h2 class="button">`, such an encapsulation would prevent a conflict.

> 我想通过使用像`button.button`之类的选择器来将一些功能块封装进特定标签中。如果最近有人在他们的代码使用`<h2 class =“button”>`，这样封装将会组织冲突的发生。

The CSS specificity of such a selector grows. `.button--mod` selector will not overwrite CSS properties of the block, only `button.button--mod` would work. You will need its modifiers to be combined with the tag as well and so do the developers who lately would redefine your block.

使用`.button--mod`选择器来增加CSS的特殊性不会覆盖块的CSS属性，只有使用`button.button--mod`才能工作。您需要将其修饰符与标签结合使用，最近将重新定义您的块的开发人员也会如此进行。

Lately, when a project goes larger, it's very likely that you may have `input.button`, `span.button` and `a.button` as well. And all the prefixed selectors for modifiers and nested elements will need 4 declarations.

随后，随着您的项目变大时，您很有可能会有`input.button`，`span.button`和`a.button`等选择器。所有修饰符和嵌套元素的前缀选择器都需要4个声明。

So, it is better not to tie your own hands with such prefixing. However if you still can softly-softly ensure that your blocks are used with proper tags if your provide your users with templates for every block. This is the most flexible and automatic solution.

所以，最好不要选择这样的前缀。但是，如果您可以确保为您的用户提供每个块的模板都有正确的属性标签。那这将会是最灵活，也最方便的解决方案。

If the templating looks overhead, there is a "documentation" approach to inform your users which tag the block CSS class would be applied to, this can be done with documenting the block code. The shortest version could be just a comment with a tag name prefixing the block declaration `/*button*/.button`. Or that can be a larger comment with full HTML piece needed to the block to function.

如果模板看起来是太过复杂的话，那么可以使用“文档”的方法来告诉您的用户哪个块的CSS类使用哪个标签，这些都可以通过在块的代码中记录完成。最短的声明可能就只是一个前缀为块声明`/*button*/.button`的标签名。或者，可能是一个带有完整的HTML代码块功能的更大的注释。

<a id="css-modifier-names"></a>
## 将修饰符命名为它们在CSS中的样式好么？（Is this good to name modifiers corresponding to what they have in CSS?）

> Thanks to mixes, we can create a lot of modifiers which represent CSS properties and assign them to blocks. But I've heard that "it is bad". For example, this selector `.block__element--border-bottom-5px` was stamped as "awful". I am wondering why and how should the modifiers be named then?

> 多亏了混合（mixes），我们可以创建很多代表CSS属性的修饰符，并将它们分配给块元素。但是我听有人说“这样做很糟糕”。例如，选择器`.block_element--border-bottom-5px`被打上了“糟糕”的名号。我想知道这是为什么，那我们又应该如何命名修饰符呢？

Naming the modifiers corresponding to their CSS representation is not recommended. Indeed it looks not very nice but there are also practical reasons against it. Lately then the view of your components is changed, you will need to fix not only CSS but also the selectors. So, when you border is 6px, it would require changes in all the templates and sometimes in JavaScript.

将修饰符命名为它们在CSS中的样式是不被推荐的。不光是因为它们看起来不合理，还有一些实际的原因反对它们。如果您要改变您的组件的视图，那您不光要修改您的CSS，还要修改选择器。所以，当您的边框是6px，那在所有的模板和一些JavaScript中都需要修改。

Also, it never happens that a modifier has only one CSS property to define and will have it forever. Even if now it is only border that differentiates one state from another, this is very likely that lately you would need other CSS properties for the same state of your block. This would be messy if you define a background or padding in a modifier called "border". So, it is recommended to choose semantic names for modifiers even if they only have one property by now.

另外，从来没有过修饰符只为一个CSS属性声明，并且永远都只为修饰这个属性而留下来。即使现在只是一个状态的边框与另一个状态的不同，之后也很有可能需要您为这个的状态再修改其他CSS属性。 如果在一个名为“border”的修饰符中定义背景或内边距的样式，这看起来会很奇怪。所以，即使现在只有一个属性，也建议选择使用修饰符的语义来定义。

<a id="css-nested-elements"></a>
## 一个在另一个元素中的元素的类名应该怎么设置？像`.block__el1__el2`这样么？（What would be a class name for an element inside another element? `.block__el1__el2`）?

> What should I do if my block has a complex structure and its elements are nested? CSS classes like `block__elem1__elem2__elem3` look scary.

> 如果我的块有一个复杂的结构，并且它拥有嵌套的子元素，我应该如何处理它们？如果将CSS类命名为`block__elem1__elem2__elem3`，那看起来也太可怕了。

According to BEM method, block structure should be flattened; you do not need to reflect nested DOM structure of the block. So, the class names for this case would be:

根据BEM的方法，块元素的结构应该是平整的; 您不需要反映该块是嵌套DOM结构。所以，这个例子的类名是：

```css
.block {}
.block__elem1 {}
.block__elem2 {}
.block__elem3 {}
```
Whereas the DOM representation of the block may be nested:

这样的DOM可以代表块元素是嵌套的结构：

```html
<div class='block'>
    <div class='block__elem1'>
        <div class='block__elem2'>
            <div class='block__elem3'></div>
        </div>
    </div>
</div>
```

Besides the fact that the classes look much nicer, it makes the elements be dependent on the block only. So, you can easily move them  across the block when providing changes to the interface. The changes of the block DOM structure would not need corresponding changes to the CSS code.

除了让类的结构看起来更好之外，它还使得子元素只依赖于块元素本身。所以，当对接口进行更改时，您可以轻松地对它们进行操作。而且，对于块的DOM结构的变化，不需要您对CSS代码做相应的改变。

```html
<div class='block'>
    <div class='block__elem1'>
        <div class='block__elem2'></div>
    </div>
    <div class='block__elem3'></div>
</div>
```

<a id="global-css-resets"></a>
## 我听说BEM不推荐使用全局CSSreset，为什么？（I've heard that BEM does not recommend global CSS resets. Why?）

> CSS resets is a practise making a good showing. Many frameworks first align anything and then apply their special styles. BEM does not recommend common resets. Why? And what we are supposed to do instead?

> CSS重置是一个很好的表现方式。许多框架首先会将任何元素进行排列，然后再应用不同的风格。BEM不推荐这种常见的重置。为什么？那我们应该如何做呢？

Nothing bad would happen to your blocks if you use common reset (well, except of some special cases below). So, BEM does not prohibit to use them. But using them BEM-way would be more effective.

如果你使用普通的重置方法（除了下面的一些特殊情况），不会对您的块产生不良的影响。所以，BEM并不禁止使用它们。但是，使用BEM自带的方式往往会比这种方式更有效。

Common CSS reset is a set of CSS to be applied to document nodes and ensure that their default view is the same in different browsers. In most cases the CSS rules are written for tag selectors and this is not recommended in BEM (you can find a lot of explanation above).

常见的CSS重置是一组应用到文档节点的CSS，并确保它们在不同的浏览器中的默认视图是相同的。在大多数情况下，CSS规则是为标签选择器编写的，这在BEM中不推荐（您可以在上面找到很多解释）。

Another point is that in BEM a block encapsulates everything which is needed for it to be displayed and function. And this is why we call the BEM blocks independent. If the block does not look properly without a third-party CSS being added onto the page, it cannot be called "independent" that much.

另一点是在BEM中，一个块会封装所需的所有功能。这就是为什么我们称BEM为独立的模块。 如果在页面上没有其他CSS加载，块看起来就会不正确，就不能称这个块为“独立”的块。

Assuming this all, BEM recommends every block to reset itself. If you have `menu` block and `list` block both as `<ul>` in your HTML, each of them should provide the reset CSS usually given to `<ul>`. You may worry that having several blocks with the same reset rules will case repeats in the resultant code. But this is what CSS optimizers should do for you. As a developer you develop every block independently, as if there are no other blocks on the same page.

除此之外，BEM还建议每个块可以重置其本身。如果在您的HTML中`menu`块和`list`块都是`<ul>`，那么它们都应该为`<ul>`提供复位的CSS。您可能会担心，具有相同重置规则的多个块会在结果代码中重复出现。但是这是CSS优化器应该为您做的。作为开发人员，您应该独立开发每个模块，就好像在同一页面上没有其他模块一样。

In the case you don't have a CSS optimizer to combine selectors with the same set of rules, you may use preprocessors to prevent copy-paste. With every new block you can make it reset itself mixing the proper code. For example, with SASS this would look like:

如果您没有关于CSS合适的优化方式将选择器与同一组规则结合使用的话，那您可以使用预处理器来防止复制粘贴。你可以在添加新块后重置代码以保证最后可以生成正确的代码。例如，在SASS中，看起来就像：

```css
.menu {
    @include reset-list;
}
.menu__item {
    @include reset-list-item;
}

/* ... */

.list {
    @include reset-list;
}
.list__item {
    @include reset-list-item;
}
```

However using this mixin-way you should realize that the only reason for it is not having a proper optimizer.

然而，您需要意识到，我们使用混合方式的唯一原因是我们现在没有合适的优化器。

Having resets for every block (besides being nice and BEMish) will also prevent problems with injecting a third-party piece of HTML/CSS markup which relies on browser defaults and so can be affected by global resets. For example, this is a known problem for webmails.

重设每个块元素（除了看起来已经合适的块元素和BEMish以外），也可以防止注入依赖于浏览器的默认的第三方HTML / CSS标记问题，这可能受到全局重置的影响。例如，这在网络邮件中，是一个已经存在的问题。

<a id="ask-your-question"></a>
## 没找到答案？请提问您的问题！（Did not find the answer? Please ask your questions!）

If you didn't find the proper answer, please [ask your question](https://github.com/getbem/getbem.com/issues/new?title=Type+your+question&body=Explain+in+detail+your+question&labels=question)!

如果您没有找到合适的问题，请[提出您的问题](https://github.com/getbem/getbem.com/issues/new?title=Type+your+question&body=Explain+in+detail+your+question&labels=question)！

