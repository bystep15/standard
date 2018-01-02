# Formatting Code

[原文](https://smacss.com/book/formatting)

Everybody has their own way. The tools and techniques that you use are ones that you have tried either through trial and error or you have tried what you heard works for other people. When I first got into development, I used Dreamweaver. It had plenty of features and allowed me to build static HTML sites quickly and efficiently. After seeing a co-worker using Ultraedit and seeing how fast he was able to get work done, I started to learn it as a way of complementing my existing tool set. The same has occurred with the way I code. I will see a technique or style that someone else uses and I will assimilate those techniques into my own way of working.

This section, Formatting Code, is a brief look at how I code my work and do so in a way that seems to work well for others having to continue working on my code.

## Single line versus multiple lines

For many years, I have coded my CSS using the [single line approach](http://orderedlist.com/resources/html-css/single-line-css/). This means that all of the properties for a given rule set are declared on the same line. This allows for quick scanning of the selectors along the left. Being able to scan selectors has traditionally been more important to me than seeing properties nicely lined up. Up until just a couple years ago, the list of properties assigned to a rule set were quite small; it would be unusual to have more than a handful. Therefore, I could find the selector I wanted and all of the properties would be visible on the screen.

With CSS3—and the myriad of vendor-specific prefixes that come with it—things can get out of hand rather quickly. Between that and working with a larger team, it was easier for everybody to have each property/value pair on its own line.



CSS3 with the plethora of vendor-prefixed properties can be too much to read easily if all on one line.

```
.module {
    display: block;
    height: 200px;
    width: 200px;
    float: left;
    position: relative;

    border: 1px solid #333;
    -moz-border-radius: 10px;
    -webkit-border-radius: 10px;
    border-radius: 10px;

    -moz-box-shadow: 10px 10px 5px #888;
    -webkit-box-shadow: 10px 10px 5px #888;
    box-shadow: 10px 10px 5px #888;

    font-size: 12px;
    text-transform: uppercase;
}
```



In the example, there are 11 properties declared and we could easily have a half-dozen more if we added another feature or two to our module. Having these all on one line would leave the first handful of properties visible on the screen and we would be left scrolling to the right to uncover the rest of the properties. This makes it hard to scan the document and see what properties have been defined.

There are a few other minor things to note with the example:

* There is a space after the colon.
* Four spaces before each declaration (no tabs).
* Properties are grouped by type.
* Opening bracket on the same line as the rule set.
* Colour declarations use the short form.

These are all preferential and I will not begrudge you for using a completely different approach. This is just what I have found that feels natural and makes the most sense to me.

## Grouping Properties

Some people organize alphabetically, others don’t organize at all, and others may use some other arbitrary system. I fall in this last category. It's not completely arbitrary, mind you. I would describe it as ordering from most important to least important but what is important when it comes to declaring styles on an element?

I organize in the following order:

1. Box
2. Border
3. Background
4. Text
5. Other

Box includes any property that affects the display and position of the box such as `display`, `float`, `position`, `left`, `top`, `height`, `width` and so on. These are most important to me because they affect the flow of the rest of the document.

Border includes `border`, the oft-unused `border-image`, and `border-radius`.

Background comes next. With the advent of CSS3 gradients, background declarations can actually become quite verbose. Once again, vendor prefixes just compound the issue.



Multiple backgrounds with CSS3 declarations.

```
background-color: #6d695c;
background-image: url("/img/argyle.png");
background-image:
  repeating-linear-gradient(-30deg, rgba(255,255,255,.1), rgba(255,255,255,.1) 1px, transparent 1px, transparent 60px),
  repeating-linear-gradient(30deg, rgba(255,255,255,.1), rgba(255,255,255,.1) 1px, transparent 1px, transparent 60px),
  linear-gradient(30deg, rgba(0,0,0,.1) 25%, transparent 25%, transparent 75%, rgba(0,0,0,.1) 75%, rgba(0,0,0,.1)),
  linear-gradient(-30deg, rgba(0,0,0,.1) 25%, transparent 25%, transparent 75%, rgba(0,0,0,.1) 75%, rgba(0,0,0,.1));
background-size: 70px 120px;
```



Complex patterns are possible with CSS3 gradients but create for lengthy background declarations, and the example doesn't even include CSS3 prefixes. Just imagine how long this declaration would be if it did!

Text declarations include `font-family`, `font-size`, `text-transform`, `letter-spacing` and any other CSS properties that affect the display of the type.

Anything that doesn’t fall into any of the above categories gets added to the end.

## Colour Declarations

This may seem like a silly thing to even mention but I have seen different developers do different things. Some like using keywords like `black` and `white` but I have always tried to stick to either the 3 digit or 6 digit hex format wherever possible. `#000` and `#FFF` are shorter, albeit barely, then their keyword counterparts. Likewise, I wouldn’t use `rgb` or `hsl`, since the hex form is shorter. Of course, `rgba` and `hsla`have no hex form and they would get used.

