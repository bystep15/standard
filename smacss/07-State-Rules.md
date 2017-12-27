# State Rules

[原文](https://smacss.com/book/type-state)

A state is something that augments and overrides all other styles. For example, an accordion section may be in a collapsed or expanded state. A message may be in a success or error state.

States are generally applied to the same element as a layout rule or applied to the same element as a base module class.



State applied to an element

```
<div id="header" class="is-collapsed">
    <form>
        <div class="msg is-error">
            There is an error!
        </div>
        <label for="searchbox" class="is-hidden">Search</label>
        <input type="search" id="searchbox">
    </form>
</div>

```



The header element just has an ID. As such we can assume that any styles, if there are any, on this element are for layout purposes and that the `is-collapsed` represents a collapsed state. One might presume that without this state rule, the default is an expanded state.

The `msg` module is simple enough and has an error state applied to it. One could imagine a success state could be applied to the message, alternatively.

Finally, the field label has a hidden state applied to hide it from sight but still keep it for screen readers. In this case, we are actually applying the state to a base element and not overriding a layout or module.

### Isnʼt it just a module?

There is plenty of similarity between a sub-module style and a state style. They both modify the existing look of an element. However, they differ in two key ways:

1. State styles can apply to layout and/or module styles; and
2. State styles indicate a JavaScript dependency.

It is this second point that is the most important distinction. Sub-module styles are applied to an element at render time and then are never changed again. State styles, however, are applied to elements to indicate a change in state while the page is still running on the client machine.

For example, clicking on a tab will activate that tab. Therefore, an `is-active` or `is-tab-active` class is appropriate. Clicking on a dialog close button will hide the dialog. Therefore, an `is-hidden` class is appropriate.

## Using !important

States should be made to stand alone and are usually built of a single class selector.

Since the state will likely need to override the style of a more complex rule set, the use of `!important` is allowed and, dare I say, recommended. (I used to say that `!important` was never needed but on complex systems, it is often a necessity.) You won’t normally have two states applied to the same module or two states that tend to affect the same set of styles, so specificity conflicts from using `!important` should be few and far between.

With that said, be cautious. Leave `!important` off until you actually and truly need it (and you will see why in this next example). Remember, the use of `!important` should be avoided for all other rule types. Only states should have it.

## Combining State Rules with Modules

Inevitably, a state rule will not be able to rely on inheritance to apply its style in the right place. Sometimes a state is very specific to a particular module where styling is very unique.

In a case where a state rule is made for a specific module, the state class name should include the module name in it. The state rule should also reside with the module rules and not with the rest of the global state rules.



State rules for modules

```
.tab {
    background-color: purple;
    color: white;
}

.is-tab-active {
    background-color: white;
    color: black;
}
```



If you are doing just-in-time loading of your CSS, generic states should be considered part of the base and global styles and loaded on initial page load. The styles for a particular module wonʼt need to be loaded until that particular module is loaded.

