SCSS Style Guide
==========

A style guide for SCSS

General syntax
---
- Don’t use units for zero values e.g. use `margin: 0;` instead of `margin: 0px;`.
- Use lowercase letters for hex colors and use three digit codes if possible e.g. `#fff` instead of `#FFFFFF`.
- Use spaces after `:` in property declarations.
- Use `//` for comment blocks instead of `/* */`.
- Avoid use of `!important` whenever possible.
- Don’t use `div` as a selector.
- Use `font-weight: 700` if you are loading webfonts with specific weights, otherwise use `font-weight: bold`.

```scss
// bad
.class-name {
  .class-name-details {
    background: #FFFFFF;
  }

  div {
    color: red;
  }

  padding: 0px;
}

// good
.class-name {
  padding: 0;

  .class-name-details { background: #fff; }
}
```

Property order
---
```scss
.class-name {
  // box model behavior
  display: inline-block;
  float: left;
  overflow: hidden;

  // position
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;

  // size
  width: 100px;
  height: 100px;

  // margin and padding
  margin: 0;
  padding: 0;

  // appearance
  background: #fff url('stripes.png') no-repeat;
  border: 1px solid $border-color;

  // text
  color: #333;
  font-size: 1rem;
  font-weight: 700;
  line-height: 1.5;
  vertical-align: middle;

  // other stuff
  cursor: move;
  opacity: 0.5;
  z-index: 9001;
}
```

Nesting order
---
```scss
.selector {                 // <- selector
  position: relative;       // <- selector properties

  @include box-shadow();    // <- SCSS mixins

  &:before { ... }          // <- selector pseudo-elements

  &:last-child { ... }      // <- selector pseudo-classes

  &.sibling-class { ... }   // <- selector siblings

  & > .child-class { ... }  // <- selector children

  .descendant-class { ... } // <- selector descendants
}
```


Nesting
---
When possible, do not nest selectors more than one level deep. Occasionally, specificity will require further nesting (common with elements such as `<ul>` and `<li>`).


Variables
---
Keep your global variables in a file called `_variables.scss` and include it at the top of your app.scss file.

Local variables in _.scss partials are okay when they cut down on changes in multiple places. For example:

```scss
$circle-diameter: 32px;
.circle {
  position: absolute;
  left: -#{$circle-diameter}
  width: $circle-diameter;
  height: $circle-diameter;
  border-radius: 50%;
}
```


Mixins
---
Keep your global mixins in _mixins.scss and include toward the top of your app.scss file.


Functions
---
Keep your global functions in _functions.scss and include toward the top of your app.scss file.


@extend
---
Avoid using `@extend`. It doesn’t work with media queries and the way it extends selectors can be unintuitive. Use mixins instead.


Media queries
---
Group media queries at the bottom of each appropriate _.scss partial. Write SCSS that is mobile-first and use media queries to target larger screens.

```scss
.button {
  display: inline-block;
  width: 100%;
}

@media "only screen and (min-width: 768px)" {
  .button { width: auto; }
}
```


Selectors
---
- Avoid abbreviations


```scss
// bad
.btn { ... }

.blog span { ... }

.className { ... }

.u-floatleft { ... }

// good
.button { ... }

.blog .label { ... }

.class-name { ... }
```


Data attributes
---
Use data- attributes to connect to javascript instead of classes. This prevents style changes from affecting javascript functionality. Don’t use data attributes for styling.

```javascript
// bad
$('.dropdown-toggle').on('click', function(ev) {});

// good
$('[data-toggle="dropdown"]').on('click', function(ev) {});
```


Text editor settings
---
- Set encoding to UTF-8.
- Use two spaces for indentation (soft tabs).
- Remove all trailing whitespace.
- Add a newline at the end of each file.
