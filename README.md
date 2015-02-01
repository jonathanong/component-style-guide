
# Component Style Guide

This is a style guide for writing (web) components.
In other words, they are a mixture of HTML, CSS, JS, images, fonts, etc.
This is an extension of the [Module Style Guide](https://github.com/jonathanong/module-style-guide).

This does not cover HTML/CSS/JS specific styles,
only how they are packaged together in a component.

## `index.*` entry points

Always include the relevant `index.*` entry points.

- `index.html`
- `index.css`
- `index.js`

In the future, all you need is `index.html`.
Even if you don't actively support web components,
you should still have an `index.html` file anyway for `<link rel="import">` anyways.

## `test/index.*` entry points

Your tests should be available at `test/index.html` and/or `test/index.js`.
When serving, you should only have to open `test/` to run the tests.

## CSS class names should match its JS constructor's name

See [SUIT CSS naming conventions](https://github.com/suitcss/suit/blob/master/doc/naming-conventions.md).

For example, if your components exports a JS module:

```js
export default Dropdown;

function Dropdown(options) {

}
```

Your class names should correspond to the constructor name, optionally with a prefix:

```css
.Dropdown {

}

.Dropdown-item {

}

.Dropdown--closed {

}
```

The more unique you make this class name, the better.

## Inline CSS if possible

CSS is global, scoped styles is not widely supported, and shadow DOM may be overkill for every component.
Inline your CSS whenever possible, or make every element have a unique ID and scope styles to that ID.

## Compile components into modules whenever possible

Although we have the concept of Web Components,
it's easier to consume components as modules.
If possible, package them as a module while still keeping assets in their native format.
For example, try to keep HTML in `.html` files and CSS in `.css` files.
