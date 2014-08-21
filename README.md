SCSS Style Guide
==========

A style guide for SCSS

Syntax
---
- Don’t use units for zero values e.g. `margin: 0;` instead of `margin: 0px;`.
- Use lowercase letters for hex colors and use three digit codes if possible e.g. `#fff` instead of `#FFFFFF`.
- Use spaces after `:` in property declarations.
- Use `//` for comment blocks instead of `/* */`.
- Avoid use of `!important` whenever possible.
- Don’t use `div` as a selector.

```scss
// bad
.class-name {
  .class-name-details {
    background: #FFFFFF;
  }

  padding: 0px;
}

// good
.class-name {
  padding: 0;

  .class-name-details { background: #fff; }
}
```

Nested structure
---
```scss
.selector { // <- selector
  position: relative; // <- selector properties

  &:before { ... } // <- selector pseudo-elements

  &:last-child { ... } // <- selector pseudo-classes

  &.sibling-class { ... } // <- selector siblings

  & > .child-class { ... } // <- selector children

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
