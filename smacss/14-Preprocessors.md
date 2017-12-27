# Preprocessors

[原文](https://smacss.com/book/preprocessors)

As great as CSS is, it is still missing features that many designers and developers would like it to have. To help fill this void—and to help speed up development—tools have been created to make our lives easier.

One type of tool is the CSS preprocessor. I’ll review what a preprocessor is, what it can do, and how it can help you in building scalable and modular CSS.

## What is a preprocessor?

A CSS preprocessor allows you to use a special syntax in your CSS that is then compiled within your project. Some preprocessors try and stick as closely as possible to actual CSS syntax, whereas others try to simplify things as much as possible.

Take a look at this example for the [Stylus](http://learnboost.github.com/stylus/) preprocessor.



Coding using Stylus

```
@import 'vendor'

body
  font 12px Helvetica, Arial, sans-serif

a.button
  border-radius 5px
```



For those who know [Ruby](http://www.ruby-lang.org/en/) or [CoffeeScript](http://coffeescript.org/), this will feel familiar. It strips out the need for curly braces and semi-colons and relies on significant white space instead. The indentation indicates which properties apply to which rules. Property names never have spaces in them, which means that the first space after the property name must separate the property from the value.

In addition to Stylus, the two preprocessors that currently lead the market are [Sass](http://sass-lang.com/) (or similarly, [Compass](http://compass-style.org/)) and [Less](http://lesscss.org/).

### Installing a preprocessor

One of the complaints, especially from designers not as familiar with the command line, is that these preprocessor tools can be complicated to install. Depending on your environment, they can be. Or, it can be as simple as dragging an application into your Applications folder.

For installing Sass on a Mac, for example, I just hopped to the command line and typed:



Installing Sass

```
sudo gem install sass
```





Or installing Compass

```
sudo gem install compass
```



[Gem](http://rubygems.org/) is a command line tool from the Ruby world that acts as a *package manager* for installing applications and is pre-installed on recent versions of Mac OS X.

Once Sass is installed on my machine, I set Sass to watch a folder that I’m working on.



Running Sass

```
sass --watch before:after
```



Where before is the folder where all my .scss (precompiled CSS files) files are contained and `after` is where the post-compiled CSS files are placed. Any changes I make to my `.scss` files in the `before` folder are automatically compiled and placed as .css files in the `after` folder. This is handy for building and testing things quickly during development. (An .scss file is like a regular .css file but using the Sass syntax which I’ll explain later in this chapter.)

There is also the [Compass Mac app](http://compass.handlino.com/) that avoids the need of doing anything at the command line.

Less uses npm, the [node package manager](https://github.com/isaacs/npm), which isn’t pre-installed. Therefore, you’d need to install both the node package manager and then Less after that. Less also has a JavaScript version that can run client-side during the development process.



Less’ Client-side Implementation

```
<link rel="stylesheet/less" type="text/css" href="styles.less"><script src="less.js"></script>
```



Remember not to deploy this to a live site. Always compile the CSS before launch.



Less Command Line Compilation

```
lessc styles.less
```



Increasingly, site development is requiring command line tools. They can be a handy way to streamline your process and even get you out of a pickle that GUI tools sometimes can’t solve.

## Useful features of a preprocessor

Preprocessors offer up plenty of interesting features that can help make authoring CSS easier. A few of them are:

* Variables
* Operations
* Mixins
* Nesting
* Functions
* Interpolation
* File importing
* Extending

What does all that mean? Let’s look deeper at some of them. (I’ll be using Sass for the examples moving forward but be aware that Less and Stylus also have similar approaches for the same concepts.)

### Variables

Anybody who has worked with CSS for more than an hour has likely wished for the ability to set a colour value once in a CSS file and then to re-use that colour anywhere else in the CSS. In Sass, you can define a variable prefacing a word with `$` and assigning it a value.



Using Variables

```
$color: #369; 

body {
    color: $color;
}

.callout {
    border-color: $color;
}
```



The compiler will then convert this into the final file for deployment.



Compiled Variables

```
body {
    color: #369;
}

.callout {
    border-color: #369;
}
```



This is very handy for keeping site-wide changes all in one place. (Of note, the W3C is working on a draft specification of [CSS Variables](http://dev.w3.org/csswg/css-variables/).)

### Nesting

When coding CSS, it’s quite common to have a selector chain.



Selector Chains

```
.nav > li {
    float: left;
}

.nav > li > a {
    display: block;
}
```



Nesting allows these styles to be grouped more clearly in the precompiled CSS file.



Nesting with Sass

```
.nav {
    > li { 
        float: left;
        > a {
            display: block;
        }
    }
}
```



Each set of styles is nested inside the one above it. What does this look like generated?



Generated CSS from Sass

```
.nav > li {
  float: left; }
  .nav > li > a {
    display: block; }
```



The nesting helps clarify which styles are grouped with what elements but not much different than just indenting the styles on your own. There is some saved typing from not having to type `.nav` every time.

### Mixins

Mixins come with a lot of power. A mixin is a group of styles that can be re-used throughout your CSS. They can take parameters that customize the output of the mixin. One of the more common uses for mixins is to handle vendor prefixes. (Although they can really be used for any repetitive CSS rules.)



An Example Mixin for `border-radius`

```
@mixin border-radius($size) {
  -webkit-border-radius: $size;
     -moz-border-radius: $size;
          border-radius: $size;
}
```



Once you’ve declared a mixin, you can then call it from anywhere within your CSS using the `include` directive.



An Example Mixin for `border-radius`

```
.callout {
    @include border-radius(5px);
}
```



The preprocessor will then compile that into this:



Generated CSS for the `border-radius` mixin

```
.callout {
  -webkit-border-radius: 5px;
     -moz-border-radius: 5px;
          border-radius: 5px;
}
```



### Functions

The Mixins example already looks like a function. There is, however, the ability to do some powerful stuff with calculating values. For example, the `lighten` function takes a colour value and a percentage and will adjust the lightness of that value.



Adjusting colour value using a function

```
$btnColor: #036;
.btn { 
    background-color: $btnColor; 
}
.btn:hover { 
    background-color: lighten($btnColor, 20%); 
}
```



The preprocessor will then compile that into this:



Compiled CSS with colour functions

```
.btn { 
    background-color: #003366; 
}
.btn:hover { 
    background-color: #0066cc; 
}
```



Sass comes with a number of handy functions like this and Compass adds even more. (*If you’re going to use Sass, I highly recommend taking advantage of Compass, too.)*

### Extensions

Extensions are the ability to extend one module with the properties of another. In Sass, this is done with the `extend` directive.



Sass Extensions

```
.btn { 
    display: block;
    padding: 5px 10px;
    background-color: #003366; 
}
.btn-default { 
    @extend .btn;
    background-color: #0066cc; 
}
```



The extension takes the styles from `btn` and applies them to `btn-default`. Sass is fairly smart, though. It doesn’t simply duplicate the rules in the second declaration. It creates a combination selector for the first set of rules.



Compiled CSS from Sass Extensions

```
.btn, .btn-default {
  display: block;
  padding: 5px 10px;
  background-color: #003366; }

.btn-default {
  background-color: #0066cc; }
```



The extensions are limited to simple selectors. You couldn’t extend `#main .btn`, for example. We will come back to discuss extensions and how they impact the SMACSS approach later on in this chapter.

### Even more

This is only the tip of the iceberg when it comes to preprocessors. There are plenty of more features and examples on the respective web sites. It may seem daunting at first. Don’t feel the need to use every feature right away.

## Getting into and out of trouble

You know the saying. “With great power comes great responsibility.” These preprocessors offer up lots of great functionality that can keep your precompiled CSS files nice and lean. However, once compiled, the magic can result in bloated CSS that is difficult to debug. In other words, you’re right back where you started. Bloated code is a possibility no matter how you code—whether by hand, by a WYSIWYG tool like Dreamweaver, or via a command line preprocessor. It’s also possible to create great code using any of these tools.

Let’s look at where we can get into trouble.

### Deep Nesting

Once you start nesting, it can easily be taken too far. Imagine, if you will, something like this:



Deep Nesting with Sass

```
#sidebar {
  width: 300px;
  .box {
    border-radius: 10px;
    background-color: #EEE;
    h2 {
      font-size: 14px;
      font-weight: bold;
    }
    ul {
      margin:0;
      padding:0;
      a {
        display:block;
      }
    }
  }
}
```



That wouldn’t be unusual to see. I’ve seen this quite a bit in working on existing Sass files. Here is what that generates into:



Compiled CSS using Deep Nesting with Sass

```
#sidebar {
  width: 300px; }
  #sidebar .box {
    border-radius: 10px;
    background-color: #EEE; }
    #sidebar .box h2 {
      font-size: 14px;
      font-weight: bold; }
    #sidebar .box ul {
      margin: 0;
      padding: 0; }
      #sidebar .box ul a {
        display: block; }
```



#### Nesting with SMACSS

The SMACSS approach, by its very nature, minimizes deep nesting due to depth of applicability. The separation of layout and modules also avoids these issues. With SMACSS, the previous example would look more like this:



Deep Nesting with SMACSS

```
#sidebar {
  width: 300px;
}

.box {
  border-radius: 10px;
  background-color: #EEE;
}

.box-header {
  font-size: 14px;
  font-weight: bold;
}

.box-body {
  margin: 0;
  padding: 0;
  a {
    display: block;
  }
}
```



There’s barely any nesting at all! That’s because we don’t need long selectors to get the styles that we want. It’s only when we need to target element selectors in a part of the module where we really need to worry about nesting.

Creating long selector chains just makes the browser work harder than it needs to when determining whether a style applies to the current element.

### Unnecessary extending

Returning back to our extension example of a default button extending from default button styles, let us look at that code example again.



Sass extension of a button

```
.btn { 
    display: block;
    padding: 5px 10px;
    background-color: #003366; 
}
.btn-default { 
    @extend .btn;
    background-color: #0066cc; 
}
```



This allows us to do the following HTML, no longer needing to specify both the `btn` and `btn-default` classes on an element. Only one needs to be specified. We move the multiple declarations to the CSS from the HTML.



Application of the class on a link

```
<a class="btn-default">My button</a>
```



Extending modules to create sub-modules are a way of avoiding having to define multiple classes in the HTML. The naming convention becomes more important in this situation. Having a module name of `btn` and a sub-module name of `small` would complicate things when the only class that gets applied is `small`. A small what? With `btn-small`, we can use the sub-module name on its own and still know what its purpose is for.

Looking at the SASS source, we can also see that the `btn-default` is a sub-module because of the use of `@extend`. Looking at the generated source, we can still see that `btn-default` is a sub-module because it will be grouped with the `btn` class.

Where extending modules fails is when we extend across disparate modules.



Sass extension across modules

```
.box { 
    border-radius: 5px;
    box-shadow: 0 0 3px 0 #000000;
    background-color: #003366; 

}
.btn { 
    @extend .box;
    background-color: #0066cc; 
}
```



Extending across modules now ties these two concerns together. There is no longer one source of truth for where the styles for a module live.

By tightly grouping everything in the CSS, you lose the ability to do just-in-time loading or to do conditional compilations depending on the components you need to load into your app. Button *and* box styles need to be loaded at the same time.

Extending even within the same module can introduce complexity to a project that does just-in-time loading of styles. For example, at Yahoo!, we would load the default button styles upon page load but only load secondary styles—such as those for compose—when that screen was requested. This kept the initial page load times very quick.

#### SMACSS Extensions

Using the SMACSS approach, extensions are just handled at the HTML level instead of the CSS level by defining the multiple classes in the HTML.



Applying SMACSS module classes on a button

```
<a class="btn btn-default">My button</a>
```



This has the added benefit of recognizing where the root element of a module is. When looking at compiled HTML in the browser, it may be difficult to discern where one module starts and where another one ends. Since root module names don't have any hyphenation, they stand out in the crowd.

I recognize that it begins to feel like *classitis* where multiple (seemingly unnecessary) classes are being added to the HTML. However, these classes aren't unnecessary. They clarify intent and increase the semantics of the element in question.

### Overused Mixins

Mixins are a handy way of avoiding repetition. However, CSS classes are also a handy way of avoiding reptition. If you have the same CSS being applied in multiple places, it may be worthwhile to move that style into its own class.

Let’s say that all a collection of modules all share a similar visual style of a gray background and a blue rounded border. You might decide to create a mixin for this.



Sass Mixin for common pattern

```
@mixin theme-border {
  border: 2px solid #039;
  border-radius: 10px;
  background-color: #EEE;
} 

.callout {
  @include theme-border;
}

.summary {
  @include theme-border;
}
```



That gets compiled into this:



Compiled CSS from Mixin

```
.callout {
  border: 2px solid #039;
  border-radius: 10px;
  background-color: #EEE; }

.summary {
  border: 2px solid #039;
  border-radius: 10px;
  background-color: #EEE; }
```



#### SMACSS for Repetitive Patterns

In this case, because it is a visual treatment being added to various containers, it’s worthwhile to place this into its own class.



Defining a class for common pattern

```
.theme-border {
  border: 2px solid #039;
  border-radius: 10px;
  background-color: #EEE;
} 

.callout {
}

.summary {
}
```



Then apply it to elements as required:



Applying the class

```
<div class="callout theme-border"></div>
<div class="summary theme-border"></div>
```



#### Parameterized Mixins

To be clear, parameterized mixins offer up a lot of power that is just not possible with CSS and there is no equivalent approach to solve this beyond creating a lot of variations. The border-radius mixin example from early in this chapter is a great example of a parameterized mixin.

## Smack that preprocessor

We’ve looked at a few common pitfalls of preprocessors in comparison to how we might accomplish it with SMACSS. The typical answer is: everything in moderation. Review the generated files and see if the final result is what you expect. If there is plenty of repetition then take a look at refactoring your approach.

Let’s look at a couple more ways in which a preprocessor can encourage better modularization of your code.

### State-based Media Queries with Nesting

As we saw in the chapter, Changing State, media queries are one of the ways in which we can detect and manage state changes. Most tutorials demonstrate with a separate style sheet and stuff all of the styles related to that state into a single file. This separates a module definition into possibly multiple files, making it more difficult to manage.

Sass allows media queries to be nested, allowing those state changes to be reflected where they belong: with the module.

Here is an example demonstrating nested media queries:



Nested Media Queries in Sass

```
.nav > li {
  width: 100%;

  @media screen and (min-width: 320px) {
      width: 100px;
      float: left;

  }

 @media screen and (min-width: 1200px) {
          width: 250px;
      }

}
```



The default state is defined and then the alternate states of that module are defined right from within that module. You can even embed media queries inside other media queries and Sass will concatenate the media query conditions.

Here is what the nested example generates into:



Compiled CSS from Nested Media Queries in Sass

```
.nav > li {
   width: 100%; }
@media screen and (min-width: 320px) {
  .nav > li {
    width: 100px;
    float: left; } }
  @media screen and (min-width: 1200px) {
    .nav > li {
      width: 250px; } }
```



Sass creates the separate media queries and embeds the selector inside them. With this particular example, I specifically chose the default state to be the *small screen *view that would match for any screen under 320px. Then I switched to a floated navigation once it reaches a specific width. Finally, it changes the width at 1200px but *does not re-declare the float.* I like this inheritence that occurs from the default state through the various media queries.

Best of all, any alternate states for your module are declared with the module.

### Organizing Your Files

Preprocessors encourage the separation of concerns that SMACSS recommends.

Here are some guidelines on how to separate the files in your project:

* Place all Base rules into their own file.
* Depending on the type of layouts you have, either place all of them into a single file or major layouts into separate files.
* Put each module into its own file.
* Depending on size of project, place sub-modules into their own file.
* Place global states into their own file.
* Place layout and module states, including media queries that affect those layouts and modules, into the module files.

With files separated in this way, it’ll make your project easier to prototype. HTML templates can be created for individual components and the CSS and template for an individual component (or even a subset of components) can be tested in isolation of each other.

Preprocessor-specific components such as mixins and variables should also be specified in their own files.



A sample directory structure

```
 +-layout/
 | +-grid.scss
 | +-alternate.scss
 +-module/
 | +-callout.scss
 | +-bookmarks.scss
 | +-btn.scss
 | +-btn-compose.scss
 +-base.scss
 +-states.scss
 +-site-settings.scss
 +-mixins.scss
```



Finally, create the primary CSS file that will include the other files. For many sites, this might mean just including all of the files into the master style sheet. For projects with conditional asset loading, you can have container files that import only the necessary files for specific screens.



Inside the master file

```
@import 
   "site-settings", 
   "mixins",
   "base",
   "states",
   "layout/grid",
   "module/btn",
   "module/bookmarks",
   "module/callout";
```



The precompiler will compile this into a single file for development or deployment.

When you’re ready to launch, create a compressed version of your CSS file for deployment. (Your environment may have build scripts for deploying the rest of the application. Be sure to integrate preprocessor compilation in that final build process.)



Command line for compressed CSS file using Sass

```
sass -t compressed master.scss master.css
```



## Post mortem on preprocessors

We looked at what a preprocessor is and how to install one. We looked at some popular features and a few of the pitfalls. Finally, we looked at how preprocessors can make organizing your project easier. Preprocessors can definitely be a beneficial part of your process.

