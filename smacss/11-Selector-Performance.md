# Selector Performance

[原文](https://smacss.com/book/selectors)

With work, I have had to do quite a bit of examination of performance. We run a number of tools over an application to determine where the bottlenecks are. One such application is [Google Page Speed](http://code.google.com/speed/page-speed/) which provides a number of recommendations to improve JavaScript and rendering performance. Before I get into its recommendations, we need to understand a little better about how browsers evaluate CSS.

## How CSS gets evaluated

### The style of an element is evaluated on element creation

We often think of our pages as these full and complete documents full of elements and content. However, browsers are designed to handle documents like a stream. They begin to receive the document from the server and can render the document before it has completely downloaded. Each node is evaluated and rendered to the viewport as it is received.



An example HTML document

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

Next, it sees a `div` element with an ID of content. Again, at this point, it thinks it is empty. It hasn’t evaluated anything else. The browser figures out the styles and then the `div` gets painted. The browser will determine if it needs to repaint the body—did the element get wider or taller? (I suspect there are other considerations but width and height changes are the most common effects child elements have on their parents.)

This process continues on until it reaches the end of the document.

For a visualization of the reflow/repaint process in Firefox, visit [http://youtu.be/ZTnIxIA5KGw](http://youtu.be/ZTnIxIA5KGw).

### CSS gets evaluated from right to left.

To determine whether a CSS rule applies to a particular element, it starts from the right of the rule and works its way left.

If you have a rule like `body div#content p { color: #003366; }` then for every element—as it gets rendered to the page—it will first ask if it is a paragraph element. If it is then it will work its way up the DOM and ask if it is a `div` with an ID of content. If it finds what it is looking for, it will continue its way up the DOM until it reaches the `body`.

By working right to left, the browser can determine whether a rule applies to this particular element that it is trying to paint to the viewport much faster. To determine which rule is more or less performant, you need to figure out how many nodes need to be evaluated to determine whether a style can be applied to an element.

## Which rules rule?

As each element gets rendered onto the page, it need to figure out which styles should be applied. Now, take a look through the Google Page Speed [recommendations](http://code.google.com/speed/page-speed/docs/rendering.html#UseEfficientCSSSelectors). There are four main rules that they consider inefficient:

* Rules with descendant selectors. E.g. `#content h3`
* Rules with child or adjacent selectors. E.g. `#content > h3`
* Rules with overly qualified selectors. E.g. `div#content > h3`
* Rules that apply `:hover` to non-link elements. E.g. `div#content:hover`

What is important to note with these recommendations is that *the evaluation of any more than a single element to determine styling is inefficient*. That means that you could only ever use a single selector in your rule: a class selector, an ID selector, an element selector, or an attribute selector. If you take this recommendation at face value, they are suggesting we go back to the days of `<p class="bodytext">`. (And if you look at the CSS that they generate on products like Search and Google Mail, they follow these recommendations.)

## Constrain yourself, don’t choke yourself

For the rest of us, I believe that we can be a little more practical and strike a balance between one end of the spectrum (adding classes and identifiers to everything) and the other (using deep selector rules creating tight coupling between HTML and CSS).

I follow three simple guidelines to help limit the number of elements that need to be evaluated:

1. Use child selectors
2. Avoid tag selectors for common elements
3. Use class names as the right-most selector

For example, `.module h3` might be okay if I know I am only going to have a dozen H3s on my page. How deep are my H3s in the DOM? Are they 4 levels down (e.g.: `html > body > #content > h3`) or are they 10 levels down (e.g.: `html > body > #content > div > div > … > h3`)? Can I limit the DOM traversal using child selectors? If I can do `.module > h3` (sorry IE6), then I know for the 12 H3s I have on my page, it will only have to evaluate 24 elements. If I do `.module div`, however, and I have 900 divs on my page (I just loaded up my inbox in Yahoo! Mail and there are 903), then I am going to have a lot more traversal. A simple `<div><div><div></div></div></div>` (3 levels deep) results in 6 evaluations. It is factorial. 4 levels deep results is 24\. 5 levels deep results is 120.

With all that said, even these simple optimizations may be overkill. Steve Souders, who works tirelessly on performance testing, examined the [performance impact of CSS selectors](http://www.stevesouders.com/blog/2009/03/10/performance-impact-of-css-selectors/) and determined (back in 2009) that the delta between the best case and the worst case was 50ms. In other words, consider selector performance but don’t waste too much time on it.

