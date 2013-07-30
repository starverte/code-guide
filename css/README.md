# CSS Coding Standards

## CSS syntax

* Use soft-tabs with two spaces
* Include one space before the opening brace of declaration blocks
* Place closing braces of declaration blocks on a new line
* Include one space after <code>:</code> in each property
* Each declaration should appear on its own line
* End all declarations with a semi-colon
* Comma-separated values should include a space after each comma
* Don't include spaces after commas in RGB or RGBa colors, and don't preface values with a leading zero
* Lowercase all hex values, e.g., <code>#fff</code> instead of <code>#FFF</code>
* Use shorthand hex values where available, e.g., <code>#fff</code> instead of <code>#ffffff</code>
* Quote attribute values in selectors, e.g., <code>input[type="text"]</code>
* Avoid specifying units for zero values, e.g., <code>margin: 0;</code> instead of <code>margin: 0px;</code>

**Incorrect example:**

````css
.selector, .selector-secondary, .selector[type=text] {
  padding:15px;
  margin:0px 0px 15px;
  background-color:rgba(0, 0, 0, 0.5);
  box-shadow:0 1px 2px #CCC,inset 0 1px 0 #FFFFFF
}
````

**Correct example:**

````css
.selector,
.selector-secondary,
.selector[type="text"] {
  padding: 15px;
  margin: 0 0 15px;
  background-color: rgba(0,0,0,.5);
  box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
}
````

Questions on the terms used here? See the [syntax section of the Cascading Style Sheets article](http://en.wikipedia.org/wiki/Cascading_Style_Sheets#Syntax) on Wikipedia.


## Declaration order

Related declarations should be grouped together in the following order:
- Display properties
 - `background`, `background-*`
 - `border`, `border-color`, `border-style`, `border-width`, `border-radius`
 - `border-top`,`border-top-*`, `border-top-*-*`
 - `border-right`,`border-right-*`
 - `border-bottom`,`border-bottom-*`, `border-bottom-*-*`
 - `border-image`, `border-image-*`
 - `border-collapse`, `border-spacing`, `empty-cells`, `table-layout`, `columns`, `column-*`
 - `box-shadow`
 - `outline`, `outline-color`, `outline-style`, `outline-width`
- Positioning properties
 - `position`, `top`, `right`, `bottom`, `left`
 - `clear`
 - `clip`, `visibility`, `z-index`
 - `margin`, `margin-*`, `padding`, `padding-*`
 - `caption-side`
- Box-model properties
 - `display`, `float`
 - `min-width`, `min-height`
 - `width`, `height`
 - `max-width`, `max-height`
 - `overflow`, `overflow-*`, `white-space`, `hanging-punctuation`, `punctuation-trim`
 - `rotation`, `rotation-point`
 - `box-*` (except `box-shadow`)
- Typography properties
 - `font`, `font-*`, `font-size-adjust`
 - `color`
 - `line-height`, `direction`, `letter-spacing`, `word-spacing`
 - `text-align`, `text-align-last`, `text-decoration`, `text-indent`, `text-transform`
 - `text-justify`, `text-outline`, `text-overflow`, `text-shadow`, `text-wrap`, `vertical-align`
 - `word-break`, `word-wrap`
 - `list-style`, `list-style-*`
- Other properties (not an exhaustive list)
 - `appearance`
 - `animation`
 - `box-flex`
 - `content`
 - `cursor`
 - `fit`
 - `hyphens`
 - `line-stacking`
 - `marquee-direction`
 - `opacity`
 - `orphans`
 - `transform`
 - `transition`


## Formatting exceptions

In some cases, it makes sense to deviate slightly from the default [syntax](#css-syntax).

### Prefixed properties

When using vendor prefixed properties, indent each property such that the value lines up vertically for easy multi-line editing.

````css
.selector {
  -webkit-border-radius: 3px;
     -moz-border-radius: 3px;
          border-radius: 3px;
}
````

In Textmate, use **Text &rarr; Edit Each Line in Selection** (&#8963;&#8984;A). In Sublime Text 2, use **Selection &rarr; Add Previous Line** (&#8963;&#8679;&uarr;) and **Selection &rarr;  Add Next Line** (&#8963;&#8679;&darr;).

### Rules with single declarations

In instances where several rules are present with only one declaration each, consider removing new line breaks for readability and faster editing.

````css
.span1 { width: 60px; }
.span2 { width: 140px; }
.span3 { width: 220px; }

.sprite {
  display: inline-block;
  width: 16px;
  height: 15px;
  background-image: url(../img/sprite.png);
}
.icon           { background-position: 0 0; }
.icon-home      { background-position: 0 -20px; }
.icon-account   { background-position: 0 -40px; }
````


## Human readable

Code is written and maintained by people. Ensure your code is descriptive, well commented, and approachable by others.

### Comments

Great code comments convey context or purpose and should not just reiterate a component or class name.

**Bad example:**

````css
/* Modal header */
.modal-header {
  ...
}
````

**Good example:**

````css
/* Wrapping element for .modal-title and .modal-close */
.modal-header {
  ...
}
````

### Class names

* Keep classes lowercase and use dashes (not underscores or camelCase)
* Avoid arbitrary shorthand notation
* Keep classes as short and succinct as possible
* Use meaningful names; use structural or purposeful names over presentational
* Prefix classes based on the closest parent component's base class

**Bad example:**

````css
.t { ... }
.red { ... }
.header { ... }
````

**Good example:**

````css
.tweet { ... }
.important { ... }
.tweet-header { ... }
````

### Selectors

* Use classes over generic element tags
* Keep them short and limit the number of elements in each selector to three
* Scope classes to the closest parent when necessary (e.g., when not using prefixed classes)

**Bad example:**

````css
span { ... }
.page-container #stream .stream-item .tweet .tweet-header .username { ... }
.avatar { ... }
````

**Good example:**

````css
.avatar { ... }
.tweet-header .username { ... }
.tweet .avatar { ... }
````

## Organization

* Organize sections of code by component
* Develop a consistent commenting hierarchy
* If using multiple CSS files, break them down by component
