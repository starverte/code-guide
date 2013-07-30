# HTML Coding Standards


## HTML syntax

* Use soft-tabs with two spaces
* Nested elements should be indented once (2 spaces)
* Opening and closing tags should line up vertically unless on a single line
* If there is only one nested element, consider placing the parent and nested element on the same line
* Always use double quotes, never single quotes
* Don't include a trailing slash in self-closing elements
* Except for `!DOCTYPE`, tags and attributes should be lowercase
* Attribute values may be title case or sentence case

**Incorrect example:**

````html
<!DOCTYPE html>
<html>
<head>
<title>Page title</title>
</head>
<body>
<img src='images/company-logo.png' alt='Company' />
<h1 class='hello-world'>Hello, world!</h1>
</body>
</html>
````

**Correct example:**

````html
<!DOCTYPE html>
<html>
  <head><title>Page title</title></head>
  <body>
    <img src="images/company-logo.png" alt="Company">
    <h1 class="hello-world">Hello, world!</h1>
  </body>
</html>
````

### Nesting elements

If nesting an element within a nested element, place a hard return between each nested element.
Place a comment in the form `<!-- .class -->` or `<!-- #id -->` right after the closing tag of the parent element.
See below:

````html
<!DOCTYPE html>
<html>
  <head><title>Page title</title></head>
  <body>
    <div class="container">
    
      <div class="row">
      <!-- A hard return normally wouldn't go here, but one is required to balance out the one after .align-left -->
        <h1>Title</h1><!-- Note that nested elements without nested elements within them do not have a hard return -->
        <p>First paragraph</p>
        <p>Second paragraph</p>
        <!-- A hard return normally wouldn't go here, but is required because the following element has nested elements-->
        <div class="align-left">
          <img src="images/company-logo.png" alt="Company">
          <caption>Hello, world!</caption>
        </div><!-- .align-left -->
        <!-- A hard return normally wouldn't go here, but is required because the preceding element has nested elements-->
      </div><!-- .row -->
      
      <div class="row">
        <h1>Title</h1>
        <p>First paragraph</p>
        <p>Second paragraph</p>
        <p>Third paragraph</p>
      </div><!-- .row -->
      
    </div><!-- .container -->
  </body>
</html>
````

Additional hard returns between elements that aren't nested is unnecessary, but accepted. Use sparingly, however, they can be useful when reading the code.

## HTML5 doctype

Enforce standards mode in every browser possible with this simple doctype at the beginning of every HTML page.

````html
<!DOCTYPE html>
````


## Pragmatism over semantics

Strive to maintain HTML standards and semantics, but don't sacrifice pragmatism. Use the least amount of markup with the fewest intricacies whenever possible.


## Attributes

HTML attributes should come in this particular order for easier reading of code.

* `class`
* `id`, `name`
* `data-*`
* `for`, `type`, `href`
* Other attributes in alphabetical order
* `style`
* Empty attributes i.e. `disabled`, `checked`, `hidden`, and `selected`

Such that your markup looks like:

````html
<input class="form-control" id="good-code" data-target="#element-two" type="radio" value="Yes" checked>
````

When using PHP to return values for an attribute, use `esc_attr( $attr )` or `esc_url( $url )` (WordPress only)

### Style attribute
Avoid using the `style` attribute when possible, using `class` or `id` instead. Never use the style attribute programmatically via PHP or JavaScript.

### Classes and IDs
 - An ID should be unique for every element. Classes, however, may be used for multiple elements.
 - Except for special cases (i.e. Twitter's Bootstrap), class and ID names should not be redundant
(i.e. `heading` for `<h1>`, or a class and ID with the same or similar name)
 - Class and ID names should never start with a number
 - Avoid underscores (`_`), abbreviations, and camelCase, using easily identifiable words separated by hyphens (`-`) instead
 - An element may have only one ID, but may have several classes, separated by spaces
 - If an element has multiple classes, order alphabetically
 - Classes and IDs are _optional_, don't use unless they are useful

**Incorrect example:**
````html
<h1 class="sctn_ttl ct" id="1topic">Do not do this</h1>
<p class="paragraph" id="1topic"> ... </p>
<p class="paragraph" id="2nd_paragraph"> ... </p>
````

**Correct example:**
````html
<h1 class="content section-title" id="do-this">Do this</h1>
<p> ... </p>
<p class="second"> ... </p>
````

## JavaScript generated markup

Writing markup in a javascript file makes the content harder to find, harder to edit, and less performant. Don't do it.
