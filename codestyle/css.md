# CSS Styleguide


## Base requirements

* UTF-8 encoding without BOM
* Unix-style line endings
* 80-characters line wide where possible
* Four (4) spaces indents, no tabs
* No trailing spaces. Empty line must contain only the line feed symbol.
* Lowercase only, except custom values in quotes, url's and HEX-values
* Single quotes
* One (1) empty line at the end of the file



## Ruleset

The standard ruleset looks like:
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
  * each ruleset starts on its own new line;
  * the opening brace ({) on the same line as the last selector;
  * one (1) space between the last selector and the opening brace ({);
  * each declaration on its own new line indented by four (4) spaces;
  * no empty lines between declarations, except grouping properties;
  * properties and values on the same line;
  * no spaces between property and colon;
  * one (1) space between colon and value;
  * each declaration ends with a semicolon;
  * no spaces between the value and the semicolon;
  * the closing brace (}) on its own new line, indented as the last declaration

Two or more selectors, separated by comma are allowed:
```CSS
.foo,
.bar,
.baz {
    display: block;
    color: red;
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
* No empty rulesets. This is wrong:
```CSS
.block {}
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
  * the "`>`" selector better than “' '“ (space) selector



## Property values

### Numbers
* No leading zero
* Maximum three (3) places after the point

### Colors
* 6-character color dash notation with colors without transparency: `#44B1C3`
* 3-character color dash notation everywhere it's possible. For example `#F60`
instead of `#FF6600`
* Functional notation for colors with opacity different than 1:
`rgba( 34, 12, 64, 0.3)`
* Colors in the dash notation are upper cased

### Other
* Values inside `url()` construction without quotes:
```CSS
.block {
    background-image: url(/img/sprite.svg);
    }
```
* No prefixed properties (it does Autoprefixer)
* No `!important` directive (there are limited cases when we can use the
`!important` rule)
* No units for zero values: `margin: 0`. This is wrong: `margin: 0px`



## Naming conventions

### Class name

  * minimum 3 symbols length;
  * always starts with a letter;
  * allowed characters: letters `(a-z)`, digits `(0-9)`, underscore `(\_)`,
    hyphen `(-)`;
  * hyphen `(-)` to separate words;
  * meaningful class names in English;
  * no word contractions:
```CSS
// Bad choice — contractions
.lnk, .itm, .idx, .arr {}

// Good choice
.link, .item, .index, .arrow {}
```
  * no abbreviations (there are exclusions):
```CSS
// Bad choice — abbreviations
.pdp, .fb, .pm {}

// Good choice
.product-page, .facebook, .panel-menu {}
```
  * strive to use place-independent names. For example, instead of a class like
    `.site-nav`, choose something like `.primary-nav`; rather than
    `.footer-links`, favour a class like `.sub-links`.
  * No class names which describe block appearance, like `.blue` or `.border`.
    Instead, favour a class like `.highlight-color`.

We use [BEM methodology](https://en.bem.info/method/) and according class names.

### Block

```CSS
.block {
    …
    }
```


### Element

```CSS
.block__element {
    …
    }
```


### Modifier

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
  * `.hidden`
  * `.invisible`
  * `.non-scrollable`
  * `.out-of-viewport`



## Media queries



## Files structure

* Each block have to be stored in their own file named as the block
* Avoid using overflow: hidden; rule, especially to clear floats



## Tools

* Settings for more popular editors (PHP Storm, Sublime Text, Atom)
* Snippets
* Bookmark to browser
