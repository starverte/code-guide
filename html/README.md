# HTML Coding Standards


## HTML syntax

* Use soft-tabs with two spaces
* Nested elements should be indented once (2 spaces)
* Always use double quotes, never single quotes
* Don't include a trailing slash in self-closing elements

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
  <head>
    <title>Page title</title>
  </head>
  <body>
    <img src="images/company-logo.png" alt="Company">
    <h1 class="hello-world">Hello, world!</h1>
  </body>
</html>
````


## HTML5 doctype

Enforce standards mode in every browser possible with this simple doctype at the beginning of every HTML page.

````html
<!DOCTYPE html>
````


## Pragmatism over semantics

Strive to maintain HTML standards and semantics, but don't sacrifice pragmatism. Use the least amount of markup with the fewest intricacies whenever possible.


## Attribute order

HTML attributes should come in this particular order for easier reading of code.

* `class`
* `id`
* `data-*`
* `for`, `type`, `href`
* Other attributes in alphabetical order

Such that your markup looks like:

````html
<a class="" id="" data-modal="" href="">Example link</a>
````

## JavaScript generated markup

Writing markup in a javascript file makes the content harder to find, harder to edit, and less performant. Don't do it.
