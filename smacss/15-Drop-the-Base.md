# Drop the Base

[原文](https://smacss.com/book/drop-the-base)

There are some elements—not many, but a few—that aren't used very often. As a result, you might think (as I have) that it is safe to style them as Base Rules expecting that their purpose will be singular and never changing. As you are likely to have read by now, things change. We can plan for change and prevent future change from complicating the work we have already done.

What elements fall prey to this potential problem? The `button`, `table`, and `input` elements are the most common ones I've seen. Let's delve into an example of what can often happen on a project.

## Table

Long gone from the web standardista's playbook is the use of tables for layout. As a result, the need to use a table on a project is often not needed.

Until one day, it is.

This first and only table that is needed is to display a certain set of data, such as a comparison table. The comparison table has a certain padding, column alignment, and borders. It looks great.



Table Styles

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



Overriding Previous Styles

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

The solution is clear: make a module.



Creating a module instead

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



The table element still has some base styles set. I have so rarely *not*needed a table to expand to fill its container. Nor have I *not* used `border-collapse: collapse`. These feel like they should be browser defaults!

Our comparison module now sits in isolation, as it should. I specified child selectors to keep the impact as small as possible. If I needed to embed a table within the table (which should generally be avoided) then I can be assured that the comparison module wouldn't impact the table embedded within. Our info module is now simplified to just two simple rules.

Overall, we used less CSS to achieve the result we wanted while at the same time being clearer with our code. Win-win.

As mentioned before, `button` and `input` elements can often suffer the same fate as tables. If the style serves a specific purpose then create a module. It'll avoid the need to override styles or rewrite old code.

