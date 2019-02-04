This is a work in progress document for the CSS/SASS best practices (guidelines for styles components css modules will be addressed separately).

## SCSS/SASS guidelines
It's easy to get a site up with no style guide lines - but eventually cleanly adding sections, changing colors, using other browsers or rendering responsive views becomes a nightmare.

By imposing a little bit of structure and some best practices we can reduce the tangled style rules that make pages difficult to manage and update.


## The Style Guide
Generally we have a variables sass file that where we set some rules for colors that are reused throughout the site.

This is a great practice but by extending the purpose of variables file by adding a few rules that are generally defined else where we will one place that defines consistent site wide attributes.

The basic properties of a style guide are colors, fonts, breakpoints, asset sizes (get some feed back if this is necessary but I think it should be - because we should have fixed asset sizes, with the exception being if we want to increase or reduce a section based on asset height - right now its the other way around and this helps impose design or client to use correctly sized images).

// Include examples here

This might go without saying but this means that a developer should never use these properties without referencing the variables in the style guide. So no hardcoded colors, etc.

## Cross Browser Mixins
There are numerous properties that require vendor prefixes to work across browsers. Often these are not addressed until we move to QA
Here is an excellent library we can use that will help us achieve cross browser compatibility.
https://github.com/matthieua/Sass-css3-mixins

## Normalize CSS
Cross browser issues don't only occur because of a lack of vendor prefixes. Some browsers not only vary in how they interpret rules, but also inject their own rules on certain elements ( looking at you safari :/).
Normalize its a great base for your css rules to work as expected across various browsers
https://necolas.github.io/normalize.css/8.0.1/normalize.css


# What about our CSS
Now that we have the basic style guide lines covered what about our css?

## Scope
On of the biggest issues we've faced is lack of scope for a component or page. Which leads to the "short blanket" problem where you fix one section and it break another. That section gets fixed and now the other section breaks.

As a rule every component (or template) should have a top level class name for that component. The convention I like to follow is `className="component-<COMPONENT_NAME>" or class="component-<COMPONENT_NAME>"`

For example an event component would look like `<div className="component-event">...</div>`

this gives us the ability to scope all SCSS rules to this and only this section
example:

```
.component-event {
  .event-header {
    margin: 0 10px;
    border: solid $grey 1px;
    background-color: $blue;
  }
  ...
}

```

The same would apply for top level page views where you call in each component/template allowing for finer control over components per page view ( but we don't want to over do this as we'll discuss later ).

## Bootstrap and Responsive design
Generally speaking we've been using bootstrap on out projects to help build our responsive layouts.

There are few common practies that we wan to avoid.

Overwriting default values.
There is a place for overwriting bootstrap values but generally this should be avoided directly.
When an HTML element has no other class but a bootstrap class its tempting to use that as selector

ex.
```
col-md-6 {
  padding: 0;
}
```

This pared with bad scope can have some serious unintended consequences, and even if scoped can break the component/template styles.

It's a much better practice to add an additional class name to the element and target that for your changes (event if its to overwrite the bootstrap class).

Speaking of columns - They make for a clean lay out for a row but have the intentional functionality of breaking the cell vertically at different breakpoints. DO NOT USE bootstrap columns unless you want this feature. otherwise you'll have odd breaks when resizing the browser.
