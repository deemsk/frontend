# CSS Styleguide


## Base requirements

* UTF-8 encoding
* Unix-style line endings
* 80-characters line wide where possible
* Four (4) spaces indents, no tabs
* No trailing spaces. Empty line must contain only the line feed symbol.
* Lowercase only, except custom values in quotes, url's and HEX-values
* Single quotes
* One (1) empty line at the end of the file



## Ruleset

* The standard ruleset looks like:
```CSS
[selector] {
    [property]: [value];
    [<—declaration—>]
    }
```
for example:
```CSS
.block {
    display: block;
    background-color: green;
    color: red;
    }
```
  * Each ruleset starts on its own new line
  * The opening brace ({) on the same line as the last selector
  * One (1) space between the selector and the opening brace ({)
  * Each declaration on its own new line indented by four (4) spaces
  * No empty lines between declarations, except grouping properties
  * Properties and values on the same line
  * No spaces between property and colon
  * One (1) space between colon and value
  * Each declaration ends with a semicolon
  * The closing brace (}) on its own new line, indented as the last
    declaration
* Two or more selectors, separated by comma are allowed:
```CSS
.foo,
.bar,
.baz {
    display: block;
    color: red;
    …
    }
```
  * Each selector on its own new line
  * No empty lines between selectors
  * Each selector in the list except the last ends with a comma
  * No spaces between selector and comma
* You can group related properties like this:
```CSS
.block {
    position: absolute;

    border-style: solid;
    border-width: 1px 0 0 1px;
    border-color: #FFF;

    background-color: #000;
    background-position: left top;
    }
```
  * One (1) empty line between groups of properties
* One (1) empty line between rulesets related to the same block
* Indent entire related rulesets to signal their relation to one another,
for example:
```CSS
.block {
    …
    }

    .block__element {
        …
        }

        .block__inner-element {
            …
            }
```



## Selectors

* Universal selector (\*) is forbidden
* No cascade selectors
  * _Exceptions_
* No selectors by ID
* No selectors by element
  * _Exceptions_
* No selectors by attribute
  * _Exceptions_



## Property values

* 6-character color dash notation with colors without transparency: `#44B1C3`
* 3-character color dash notation everywhere it's possible. For example `#F60`
instead of `#FF6600`
* Functional notation for colors with opacity different than 1:
`rgba( 34, 12, 64, 0.3)`
* Colors in the dash notation are upper cased
* Values inside url() construction without quotes:
```CSS
.block {
    background-image: url(/img/sprite.svg);
    }
```
* No prefixed properties (it does Autoprefixer)
* No !important directive (there are limited cases when we can use the !important rule)



## Naming conventions

* Class name
  * Minimum 3 symbols
  * Always starts with a letter
  * Allowed characters: letters (a-z), digits (0-9), an underscore (\_),
    a hyphen (-)
  * A hyphen (-) to separate words
  * Meaningful class names in English
  * No word contractions and abbreviations
  * Strive to use place-independent names. For example, instead of a class like
    `.site-nav`, choose something like `.primary-nav`; rather than
    `.footer-links`, favour a class like `.sub-links`.
  * No class names which describe block appearance, like `.blue` or `.border`.
    Instead, favour a class like `.highlight-color`.
* BEM
  * Block:
```CSS
.block {
    …
    }
```
  * Element:
```CSS
.block__element {
    …
    }
```
  * Modifier:
```CSS
.block_modifier-name_modifier-value {
    …
    }
```



## Comments

* Begin every new major section of a CSS project with a title:

```CSS
/*——————————————————————————————————————————————————————*\
    #SECTION-TITLE
\*——————————————————————————————————————————————————————*/

.selector {
    …
    }
```



## Global classes

* We have limited number of global classes which can be applied to any element.
The exhaustive list of these kind of classes listed below:
  * .hidden
  * .invisible
  * .non-scrollable
  * .out-of-viewport



## Media queries



## Files structure

* Each block have to be stored in their own file named as the block



## Recommendations

* The “>” selector better than “ “ (space) selector
* Avoid using overflow: hidden; rule, especially to clear floats



## Tools

* Settings for more popular editors (PHP Storm, Sublime Text, Atom)
* Snippets
* Bookmark to browser
