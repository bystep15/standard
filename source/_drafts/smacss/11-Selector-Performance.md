# 选择器性能（elector Performance）

[原文](https://smacss.com/book/selectors)

With work, I have had to do quite a bit of examination of performance. We run a number of tools over an application to determine where the bottlenecks are. One such application is [Google Page Speed](http://code.google.com/speed/page-speed/) which provides a number of recommendations to improve JavaScript and rendering performance. Before I get into its recommendations, we need to understand a little better about how browsers evaluate CSS.

在工作中，我不得不做许多关于性能的检测。我们通常在应用程序上运行一系列工具，以此来确定性能瓶颈在哪。[Google Page Speed](http://code.google.com/speed/page-speed/)就是这样一个应用程序，它可以提供许多改进JavaScript和渲染性能的方法。在我提出建议之前，我认为我们最好先了解一下浏览器是如何评估CSS的。

## 如何评估CSS（How CSS gets evaluated）

### 在元素创建时评估元素的样式（The style of an element is evaluated on element creation）

We often think of our pages as these full and complete documents full of elements and content. However, browsers are designed to handle documents like a stream. They begin to receive the document from the server and can render the document before it has completely downloaded. Each node is evaluated and rendered to the viewport as it is received.

我们经常认为我们的页面是充满着完整的元素和内容的文档。但是，浏览器被设计为处理像流一样来处理这些文档。开始时它会从服务器端接收文档，并可以在文档完全下载之前渲染文档。随着整个文档都被浏览器接收到的过程中，每个节点都会被评估并渲染在窗口上。

一个HTML文档的范例（An example HTML document）

```
<body>
   <div id="content">
      <div class="module intro">
         <p>Lorem Ipsum</p>
      </div>
      <div class="module">
         <p>Lorem Ipsum</p>
         <p>Lorem Ipsum</p>
         <p>Lorem Ipsum <span>Test</span></p>
      </div>
   </div>
</body>
```

The browser starts at the top and sees a `body` element. At this point, it thinks it is empty. It hasn’t evaluated anything else. The browser will determine what the computed styles are and apply them to the element. What is the font, the color, the line height? After it figures this out, it paints it to the screen.

浏览器会从文档最上方开始渲染，并会先看到`body`元素。此时，会认为`body`元素是空的，浏览器不会对`body`元素就行评估。随后浏览器会用来确定的计算后的样式，并将它们应用到元素。其中会包括什么是字体，颜色，行高。当得到这些数据后，浏览器会将数据呈现到屏幕上。

Next, it sees a `div` element with an ID of content. Again, at this point, it thinks it is empty. It hasn’t evaluated anything else. The browser figures out the styles and then the `div` gets painted. The browser will determine if it needs to repaint the body—did the element get wider or taller? (I suspect there are other considerations but width and height changes are the most common effects child elements have on their parents.)

随后，浏览器会看到一个带有ID为content的`div`元素。同上，此时，浏览器认为它是空的。它没有包含任何东西。然后浏览器会算出样式并绘制`div`。接下来浏览器会决定是否需要重新绘制body - bod元素是变宽了还是变高了？（我认为可能还有其他的考虑因素，但是宽度和高度的变化通常是子元素对父元素最常见的影响形式。）

This process continues on until it reaches the end of the document.

以上过程会持续到文档结束。

For a visualization of the reflow/repaint process in Firefox, visit [http://youtu.be/ZTnIxIA5KGw](http://youtu.be/ZTnIxIA5KGw).

有关Firefox中重排/重绘的可视化过程，请访问[http://youtu.be/ZTnIxIA5KGw](http://youtu.be/ZTnIxIA5KGw)。

### CSS从右向左进行评估（CSS gets evaluated from right to left.）

To determine whether a CSS rule applies to a particular element, it starts from the right of the rule and works its way left.

我们会从最右侧的规则开始向左查看，以此来确定CSS规则是否应用到特定的元素上。

If you have a rule like `body div#content p { color: #003366; }` then for every element—as it gets rendered to the page—it will first ask if it is a paragraph element. If it is then it will work its way up the DOM and ask if it is a `div` with an ID of content. If it finds what it is looking for, it will continue its way up the DOM until it reaches the `body`.

如果您有一个规则，如`body div＃content p {color：＃003366; }`，然后对于被呈现到页面上的每个元素，浏览器会首先查看它是不是段落元素。如果是这样的话，它会在DOM上进行渲染，然后询问它是否是带有ID为content的`div`元素。如果它符合上述标准，它会继续沿着DOM进行寻找，直到它到达`body`。

By working right to left, the browser can determine whether a rule applies to this particular element that it is trying to paint to the viewport much faster. To determine which rule is more or less performant, you need to figure out how many nodes need to be evaluated to determine whether a style can be applied to an element.

通过从右向左查看，浏览器可以确定一个规则是否适用于这个特定的元素，从而可以更快地绘制到视窗上。要确定它符合哪个规则或多或少需要一定性能的，您需要计算出需要评估多少个节点，以确定样式是否可以应用于元素。

## 什么决定了规则？（Which rules rule?）

As each element gets rendered onto the page, it need to figure out which styles should be applied. Now, take a look through the Google Page Speed [recommendations](http://code.google.com/speed/page-speed/docs/rendering.html#UseEfficientCSSSelectors). There are four main rules that they consider inefficient:

当每个元素被渲染到页面上时，它需要确定应该应用哪种样式。现在，基于Google Page Speed提出的[建议](http://code.google.com/speed/page-speed/docs/rendering.html#UseEfficientCSSSelectors)。 提出了四条认为是低效的主要规则：

* Rules with descendant selectors. E.g. `#content h3`
* Rules with child or adjacent selectors. E.g. `#content > h3`
* Rules with overly qualified selectors. E.g. `div#content > h3`
* Rules that apply `:hover` to non-link elements. E.g. `div#content:hover`

* 后代选择器。例如`#content h3`
* 子代选择器或相邻选择器。例如`#content > h3`
* 过度精确的选择器。例如`div＃content> h3`
* 添加`:hover`到非链接的元素。例如`div#content:hover`

What is important to note with these recommendations is that the evaluation of any more than a single element to determine styling is inefficient. That means that you could only ever use a single selector in your rule: a class selector, an ID selector, an element selector, or an attribute selector. If you take this recommendation at face value, they are suggesting we go back to the days of `<p class="bodytext">`. (And if you look at the CSS that they generate on products like Search and Google Mail, they follow these recommendations.)

这些建议中值得注意的一点是，通过评估任何不止一个元素来确定样式的方式是没有意义的。这意味着您可能在规则中只使用单个选择器：一个类选择器，一个ID选择器，一个元素选择器或是一个属性选择器。如果你采取这个建议，那我们就又回到使用`<p class =“bodytext”>`的日子了。 （如果您看看他们在Search和Google Mail等产品上生成的CSS，您会发现他们就会遵循这些建议。）

## 克制自己，不要想一口吃成个大胖子（Constrain yourself, don’t choke yourself）

For the rest of us, I believe that we can be a little more practical and strike a balance between one end of the spectrum (adding classes and identifiers to everything) and the other (using deep selector rules creating tight coupling between HTML and CSS).

对于我们来说，我相信我们可以做得更实际一点，并且在一端（为所有元素都添加上类和标识符）和另一端（使用深度选择器的规则在HTML和CSS之间创建紧密耦合）之间取得平衡。。

I follow three simple guidelines to help limit the number of elements that need to be evaluated:

1. Use child selectors
2. Avoid tag selectors for common elements
3. Use class names as the right-most selector

我认为以下三条简单的规范可以帮助我们限制需要评估的元素的数量。

1. 使用子类选择器
2. 避免为公有元素添加标签选择器
3. 使用类来作为最后侧的选择器

For example, `.module h3` might be okay if I know I am only going to have a dozen H3s on my page. How deep are my H3s in the DOM? Are they 4 levels down (e.g.: `html > body > #content > h3`) or are they 10 levels down (e.g.: `html > body > #content > div > div > … > h3`)? Can I limit the DOM traversal using child selectors? If I can do `.module > h3` (sorry IE6), then I know for the 12 H3s I have on my page, it will only have to evaluate 24 elements. If I do `.module div`, however, and I have 900 divs on my page (I just loaded up my inbox in Yahoo! Mail and there are 903), then I am going to have a lot more traversal. A simple `<div><div><div></div></div></div>` (3 levels deep) results in 6 evaluations. It is factorial. 4 levels deep results is 24.5 levels deep results is 120.

例如，如果我知道我只打算在我的网页上添加十几个h3的话，`.module h3`也许是个不错的选择。页面上的h3在DOM中有多深？他们是在四层结构下（例如：`html > body > #content > h3`）还是再10层结构下（例如：`html > body > #content > div > div > … > h3`）？我可以使用子类选择器来限制DOM遍历吗？如果我可以使用`.module> h3`（在IE6中无法实现），那么我知道对于在我的页面上的12个h3，只需要评估24个元素即可。但是，如果我使用`.module div`，但是在我的页面上有900个div（我只是在Yahoo! Mail中加载了我的收件箱，我发现有903个div），那么我不得不做更多的遍历。一个简单的`<div> <div> <div> </ div> </ div>`（深度为3级）就会导致6次评估。它是阶乘性的。4级层次的结果是24. 5级层次的结果是120级。

With all that said, even these simple optimizations may be overkill. Steve Souders, who works tirelessly on performance testing, examined the [performance impact of CSS selectors](http://www.stevesouders.com/blog/2009/03/10/performance-impact-of-css-selectors/) and determined (back in 2009) that the delta between the best case and the worst case was 50ms. In other words, consider selector performance but don’t waste too much time on it.

尽管如此，即使是这些简单的优化，也可能是矫枉过正的。在性能测试方面一致努力工作的Steve Souders测试了[CSS选择器的性能影响](http://www.stevesouders.com/blog/2009/03/10/performance-impact-of-css-selectors)，并确定了（早在2009年）最佳情况与最坏情况之间的差异只有50ms。换句话说，您可以去考虑选择器的性能，但不要在上面浪费太多的时间。

