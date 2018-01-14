# 从基本规则中分离（Drop the Base）

[原文](https://smacss.com/book/drop-the-base)

There are some elements—not many, but a few—that aren't used very often. As a result, you might think (as I have) that it is safe to style them as Base Rules expecting that their purpose will be singular and never changing. As you are likely to have read by now, things change. We can plan for change and prevent future change from complicating the work we have already done.

除了前面几章内容所说之外内容，还有一些元素 - 这些元素不是很多，而且并不常用。因此，您可能会（像我一样）认为将它们定义为基本规则是安全的，并希望它们的目的是单一的，永不改变。正如您现在已经阅读到的内容，事情是会发生改变的。我们可以改变为改变做出计划，以防止将来的改变使我们已经完成的工作复杂化。

What elements fall prey to this potential problem? The `button`, `table`, and `input` elements are the most common ones I've seen. Let's delve into an example of what can often happen on a project.

什么元素会陷入这个潜在的问题呢？`button`，`table`和 `input`是我见过的最常见的元素。接下来让我们来深入一个项目来看看那些经常发生的问题。

## 表格（Table）

Long gone from the web standardista's playbook is the use of tables for layout. As a result, the need to use a table on a project is often not needed.

从web标准化开始就不再使用表格进行布局。 因此，通常不需要在项目上使用表格。

Until one day, it is.

但是直到有一天

This first and only table that is needed is to display a certain set of data, such as a comparison table. The comparison table has a certain padding, column alignment, and borders. It looks great.

第一个也是唯一需要用表的地方是显示一组数据，比如一个比较表单。这个比较表有一定的内边距，列的排列和边界。并且效果看起来不错。

表格样式（Table Styles）

```
table {
    width: 100%;
    border: 1px solid #000;
    border-width: 1px 0;
    border-collapse: collapse;
}

td {
    border: 1px solid #666;
    border-width: 1px 0;
}

td:nth-child(2n) {
    background-color: #EEE;
}

```

A few days, weeks, or months later, there's a need to add another table in. This time, however, it serves another purpose. Headers on the left, data on the right. The borders are getting dropped and backgrounds are changing. Normally what we'd see here is an overriding of the default styles.

几天，几周或几个月后，需要添加另一个表单。但是，这一次，表单有其他目的。左侧放置标题，右侧放置数据。边框会降低，背景也会发生变化。 通常我们在这里看到的是重写的默认样式。

重写之前的样式（Overriding Previous Styles）

```
table.info {
    border-width: 0;
}

td.info {
    border-width: 0;
}

td.info:nth-child(2n) {
    background-color: transparent;
}

.info > tr > th {
    text-align: left;
}

.info > tr > td {
    text-align: right; 
}

```

The problem is that we've overriding styles because the base rules were designed for a singular purpose. The base rules should be designed for how we want them to appear as the default style and then augment them for specific modules. The comparison table was a module. It served a singular purpose and had a custom design, even if it was the only occurrence of the elements used in that module.

问题是，我们已经重写了风格，因为基本规则是为了一个单一的目的而设计的。基本规则应该设计为我们希望的默认样式而出现，然后在特定模块中使用它们。比较表单是一个模块。它提供了一个单一的目的，并有自定义的设计，即使它在该模块中只出现过一次。

解决办法很简单：创建一个模块（The solution is clear: make a module.）

创建一个模块（Creating a module instead）

```
table {
    width: 100%;
    border-collapse: collapse;
}

.comparison {
    border: 1px solid #000;
    border-width: 1px 0;
}

.comparison > tr > td {
    border: 1px solid #666;
    border-width: 1px 0;
}

.comparison > tr > td:nth-child(2n) {
    background-color: #EEE;
}

.info > tr > th {
    text-align: left; 
}

.info > tr > td {
    text-align: right; 
}

```

The table element still has some base styles set. I have so rarely not needed a table to expand to fill its container. Nor have I not used `border-collapse: collapse`. These feel like they should be browser defaults!

表格元素仍然有一些基本样式设置。我既不需要一个表格去扩充它的容器。也没有使用`border-collapse: collapse`属性。 因为它们被认为这是浏览器的默认的样式！

Our comparison module now sits in isolation, as it should. I specified child selectors to keep the impact as small as possible. If I needed to embed a table within the table (which should generally be avoided) then I can be assured that the comparison module wouldn't impact the table embedded within. Our info module is now simplified to just two simple rules.

我们的比较模块现在应该是单一的。我指定了子类选择器来以尽可能降低影响。如果我需要在表格中嵌入一个表格（通常应该避免这样做），那么我可以确信，比较模块不会影响嵌入的表格。我们的信息模块现在可以简化为两个简单的规则。

Overall, we used less CSS to achieve the result we wanted while at the same time being clearer with our code. Win-win.

总体而言，我们使用较少的CSS来实现我们想要的结果，同时也让我们的代码更加清晰，达到双赢的结果。

As mentioned before, `button` and `input` elements can often suffer the same fate as tables. If the style serves a specific purpose then create a module. It'll avoid the need to override styles or rewrite old code.

正如前面所提到的，`button`和`input`元素经常会遭受和表单一样的情况。如果您的样式是出于特定目的，您需要创建一个模块。这将避免重写样式或重写旧代码时所遇到的问题。
