# Depth of Applicability

[原文](https://smacss.com/book/applicability)

When learning the inner workings of CSS, we learn that we have selectors and that we use selectors to select the HTML elements on the page that we want to style. CSS has grown over the years to give us more power using an ever increasing number of selectors. Each rule set that we add to our style sheet, however, creates an ever increasing connection between the CSS and the HTML.

Let’s review a typical block of CSS that you might find on a web site.



How we tightly couple our CSS to our HTML

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

Where have I gone wrong? There are two particular concerns with the example CSS:

1. I am relying heavily on a defined HTML structure.
2. The depth of HTML to which the selectors apply is too deep.

## Minimizing the Depth

HTML is like a tree structure of parents and children. The depth of applicability is the number of generations that are affected by a given rule. For example, `body.article > #main > #content > #intro > p > b` would have a depth of applicability of 6 generations. If this selector was written as `.article #intro b` then the depth is still the same: 6 generations.

The problem with such a depth is that it enforces a much greater dependency on a particular HTML structure. Components on the page can’t be easily moved around. If we look back at the sidebar example, how do we recreate that module in another part of the page such as a footer? We have to duplicate the rules.



Duplication of rules

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



Simplification of rules

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

An advantage to using this shallow depth of applicability approach is also the ability to more readily convert these modules into templates for dynamic content. At Yahoo!, for example, we’ve been relying on Mustache for much of our template needs. Here is how we would set up our template for these pods:



An example Mustache template

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

To go even further on this last example, this design pattern is a common one. It is a container with a header and a body. (Sometimes, you will have a footer, too.) We have a `ul` in there right now but in other examples, we might see an `ol` or a `div` in its place.

Once again, we can duplicate our rules for each variation.



Duplication of rules

```

.pod > ul, .pod > ol, .pod > div {
    margin-bottom: 5px; 
} 

```



Alternatively, we can classify the pod body.



Simplifying with a class

```

.pod-body {
    margin-bottom: 5px; 
} 

```



With the module rule approach, it is not even necessary to specify the `.pod` class. We can visually see that `.pod-body` is associated with the pod module and from a code perspective, it’ll work just fine.



An example Mustache template

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

