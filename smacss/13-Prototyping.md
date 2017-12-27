# Prototyping

[原文](https://smacss.com/book/prototyping)

Good programmers like patterns. Good designers like patterns, too. Patterns establish familiarity and encourage re-use. SMACSS is about identifying the patterns in your design and codifying them.

A prototype should assist in viewing components in part or in whole and to allow the codification of the design language into building blocks. The web design industry likes reusable components and can be seen in many of the frameworks like [Bootstrap](http://twitter.github.com/bootstrap/) (for a variety of site components) and [960.gs](http://960.gs/) (for layout grids).

At Yahoo!, the prototyping team creates these building blocks and use them for production. This allowed for greater consistency across multiple products since they were all based on exactly the same foundation.

## Goals of a prototype

A prototype can serve multiple goals:

* show states
* review localization
* isolate dependencies

### States

From the default state to collapsed states to error states to whatever states you have defined, it is important to be able to visualize each of these states and make sure that the module is built accurately.

If a module is data-driven then real or mock data can be used within your prototype to test that it will render correctly.

### Localization

For projects that need to support multiple locales, it will be valuable to be able to test modules using strings from the different locales to ensure layouts don’t break as a result.

### Dependencies

Lastly, it is important to isolate dependencies. What CSS and JavaScript dependencies are required to render a module correctly? In larger projects where lazy loading is used, being able to isolate dependencies to the bare minimum required means that you have built a module effectively and can integrate that module into the site without negatively impacting other modules on the page.

At Yahoo!, modules are isolated into individual CSS files and are bundled using a combo handler when needed. For example, when the inbox loads, it combines CSS files together for buttons, message list, sidebar, tabs, and the header. The moment the user requests the Search page, the combo handler combines search-specific styles and delivers them over the pipe. Search uses a variation of the default message list and sidebar which means it only has to load the sub-classed modules.

## Pieces of the puzzle

At Yahoo!, we built a prototyping engine to help facilitate this process. Whether you need something similar will depend on the size of your project.

The prototype engine uses a [mustache template](http://mustache.github.com/) as the root. Mock data is stored in a JSON file, localization strings are stored in key/value pairs in a text file, and CSS and JavaScript dependencies are pulled in as needed. This allows the team to view a menu or a dialog or a form by itself or in the context of the entire site. In doing so, everybody can review functionality and design before going into engineering. We can also shift assets to engineering knowing that integration will be more seamless as a result.



The Yahoo! Prototype Engine

![The prototype workflow.](media/prototype-1.png)

In the case of our prototype engine, some state management is handled before the module gets rendered. This handles conditional items, data filtering and anything else that might normally be handled via server-side processing. State management isn’t always just a case of applying a class name to an HTML element.

## Your Prototype

Having a full-blown engine to compile your modules could very well be unnecessary, especially for a small site. It is still advantageous to isolate your components into an easy-to-review format. MailChimp, for example, has [an internal cheat sheet of design patterns](http://www.flickr.com/photos/aarronwalter/5579386649/) that they use to build the site. This documents various modules that are used throughout the site and the code required for each module.

Remember, patterns are good. Codifying those patterns is also good. Having a process in place to review and test those patterns is great!

