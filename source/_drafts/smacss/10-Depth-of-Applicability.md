# 适用性的深度（Depth of Applicability）

[原文](https://smacss.com/book/applicability)

When learning the inner workings of CSS, we learn that we have selectors and that we use selectors to select the HTML elements on the page that we want to style. CSS has grown over the years to give us more power using an ever increasing number of selectors. Each rule set that we add to our style sheet, however, creates an ever increasing connection between the CSS and the HTML.

在学习CSS的内部工作时，我们知道我们可以使用选择器，并且我们可以使用选择器来选择我们想要在页面上展示的HTML元素。多年来，CSS一直在发展，我们可以使用越来越多的选择器，这也给了我们更多的选择。然而，我们添加到样式表中的每个规则集都会在CSS和HTML之间建立更多关联。

Let’s review a typical block of CSS that you might find on a web site.

让我们回顾一下您可能在一个网络站点中看到的典型的CSS块。

我们是如何紧紧的关联我们的CSS和HTML代码（How we tightly couple our CSS to our HTML）

```
#sidebar div {
    border: 1px solid #333;
}

#sidebar div h3 { 
    margin-top: 5px;
}

#sidebar div ul {
    margin-bottom: 5px; 
} 

```
By looking at this, you can see that there is some expectation of what our HTML will look like. There is likely one or more sections in a sidebar that have a heading and an unordered list that follows it. If the site doesn’t change very often, this style of CSS will work just fine. I haven’t changed the design of my blog in two years. My need to scale just isn’t there. If I tried using this approach on a larger site, which can change more frequently and have a greater variety of code requirements, I am going to have problems. I will need to add more rules with more complex selectors. I may find myself in a maintenance nightmare.

通过以上范例，您可能会预测我们的HTML代码会扩展成什么样子。在侧边栏中可能有一个或多个部分，每个部分中都会有一个标题和无需列表。如果网站不经常更改，这种CSS的风格将会表现得很好。 两年来我都没有改变过我的博客的设计。我并不需要在这里进行扩展。但是如果我尝试在一个更大，改动更频繁且有更大代码需求的站点上使用这种方法，我就会遇到问题了。我需要添加更多的规则和更复杂的选择器来维持网站的正常运行。到那时我可能会发现自己会处于维护网站的烦恼中了。

Where have I gone wrong? There are two particular concerns with the example CSS:

1. I am relying heavily on a defined HTML structure.
2. The depth of HTML to which the selectors apply is too deep.

我哪里做错了呢？对于范例中的CSS，以下有两个需要关注的点：

1. 我非常依赖于定义的HTML结构。
2. 应用选择器的HTML的深度太深。

## 降低深度（Minimizing the Depth）

HTML is like a tree structure of parents and children. The depth of applicability is the number of generations that are affected by a given rule. For example, `body.article > #main > #content > #intro > p > b` would have a depth of applicability of 6 generations. If this selector was written as `.article #intro b` then the depth is still the same: 6 generations.

HTML就像父元素和子元素的树状结构。适用性的深度是受特定规则影响的纵向结构层次的数量。例如，`body.article> #main> #content> #intro> p> b`具有6层适用深度。如果这个选择器被写成`.article #intro b`，那么深度仍然是相同的，也就是6层。

The problem with such a depth is that it enforces a much greater dependency on a particular HTML structure. Components on the page can’t be easily moved around. If we look back at the sidebar example, how do we recreate that module in another part of the page such as a footer? We have to duplicate the rules.

这种深度的问题在于，它对特定的HTML结构有更大的依赖性。因为页面上的组件不能轻易移动。如果回顾一下侧边栏的那个例子，我们如何在页面的另一部分（如页脚）重新创建该模块？这就意味着我们必须复制规则。

复制规则（Duplication of rules）

```
#sidebar div, #footer div {
    border: 1px solid #333;
}

#sidebar div h3, #footer div h3 { 
    margin-top: 5px;
}

#sidebar div ul, #footer div ul {
    margin-bottom: 5px; 
} 

```

The root node is at the `div` and it is from here that we should be creating our styles.

根节点在`div`上，我们应该从这里创建我们自己的样式。

简化规则（Simplification of rules）

```
.pod {
    border: 1px solid #333;
}

.pod > h3 { 
    margin-top: 5px;
}

.pod > ul {
    margin-bottom: 5px; 
} 

```

The pod is a container that still relies on a particular HTML structure but it is of a much shallower depth than what we had before. The trade-off is that we have to repeat the pod class on numerous elements on the page. Whereas before, we just had two elements with IDs. Of course, we want to avoid going back to the days where we did silly things like adding class names to every paragraph.

pod是一个仍然依赖特定HTML结构的容器，但是它的深度比我们以前的深度要浅得多。所以方法是我们必须在页面上的许多元素上重复pod类。在此之前，我们只有两个拥有ID的元素。当然，我们要避免重犯那些愚蠢的事情，例如为每个段落添加类名。

An advantage to using this shallow depth of applicability approach is also the ability to more readily convert these modules into templates for dynamic content. At Yahoo!, for example, we’ve been relying on Mustache for much of our template needs. Here is how we would set up our template for these pods:

使用这种浅层次的适用性方法的好处还在于它能够更容易地将这些模块转换为动态内容的模板。例如，在雅虎，我们一直依靠Mustache来满足我们的大部分模板需求。以下代码是我们将如何为这些pod设置模板：

一个Mustache模板范例（An example Mustache template）

```
<div class="pod">
    <h3>{{heading}}</h3>
    <ul>
        {{#items}}
        <li>{{item}}</li>
        {{/items}}
    </ul>
</div> 
```

We are trying to strike a balance between maintenance, performance, and readability. Going too deep may mean less “classitis” within your HTML but it increases the maintenance and readability overhead. Likewise, you don’t want (or need) classes on everything. Adding classes to the `h3` or `ul` in this example would have been a little unnecessary unless we needed to have an even more flexible system.

我们正试图在可维护性，性能和可读性之间找到一个平衡点。层数太深意味着在您的HTML有更低的独特性，但它增加了维护和可读性的开销。同样，您不向（或不需要）所有东西都有类属性。除非我们需要更灵活的系统，否则在这个例子中将类添加到`h3`或`ul`中会有点不必要。

To go even further on this last example, this design pattern is a common one. It is a container with a header and a body. (Sometimes, you will have a footer, too.) We have a `ul` in there right now but in other examples, we might see an `ol` or a `div` in its place.

在最后一个例子中，我们更进一步，我们认为这种设计模式是常见的。它是一个带有标题和正文的容器。（有的时候，您也会有一个页脚。）在现在的例子里我们在这处地方看到了`ul`，但在其他的例子中，我们可能会在同一地方看到一个`ol`或`div`。

Once again, we can duplicate our rules for each variation.

再一次，我们可以为每个变动复制我们的规则。

复制规范（Duplication of rules）

```

.pod > ul, .pod > ol, .pod > div {
    margin-bottom: 5px; 
} 

```

Alternatively, we can classify the pod body.

相对的，我们可以将pod主体归为一类。

使用类来简化（Simplifying with a class）

```

.pod-body {
    margin-bottom: 5px; 
} 

```

With the module rule approach, it is not even necessary to specify the `.pod` class. We can visually see that `.pod-body` is associated with the pod module and from a code perspective, it’ll work just fine.

通过使用模块规则这种方法，我们甚至不需要指定`.pod`类。我们可以直观地看到`.pod-body`与pod模块相关联，并且从代码的角度来看，它可以正常工作。

一个Mustache模板的范例（An example Mustache template）

```
<div class="pod">
    <h3>{{heading}}</h3>
    <ul class="pod-body">
        {{#items}}
        <li>{{item}}</li>
        {{/items}}
    </ul>
</div> 
```

As a result of this small change, we were able to reduce the depth of applicability to the shallowest it can go. The single selector also means that we are avoiding potential specificity issues, too. All around, that is win-win.

通过这一小小的变化，我们能够将适用性的深度降到最小。单一选择器也意味着我们也在避免潜在的特殊性问题。从这个角度考虑，这是一种双赢的选择。
