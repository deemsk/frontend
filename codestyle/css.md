# CSS code style

## Table of content

1. [Base requirements](#base)
2. [Ruleset](#ruleset)
3. [Selectors](#selectors)
4. [Property values](#values)
  1. [Numbers](#values_numbers)
  2. [Colors](#values_colors)
  3. [Others](#values_others)
5. [BEM](#bem)
  1. [Naming conventions](#bem_naming)
  2. [Block](#bem_block)
  3. [Element](#bem_element)
  4. [Modifier](#bem_modifier)
6. [Comments](#comments)
7. [Media queries](#media-queries)


<a id="base"></a>
## Base requirements

* UTF-8 encoding without BOM;
* unix-style line endings;
* 80-characters line wide where possible;
* four (4) spaces indents, no tabs;
* no trailing spaces (empty line must contain only the line feed symbol);
* lowercase only, except custom values in quotes, url's and HEX-values;
* single quotes;
* one (1) empty line at the end of the file;



<a id="ruleset"></a>
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
* the opening brace (`{`) on the same line as the last selector;
* one (1) space between the last selector and the opening brace (`{`);
* each declaration on its own new line indented by four (4) spaces;
* no empty lines between declarations, except grouping properties;
* properties and values on the same line;
* no spaces between property and colon (`:`);
* one (1) space between colon (`:`) and value;
* each declaration ends with a semicolon (`;`);
* no spaces between the value and the semicolon (`;`);
* the closing brace (`}`) on its own new line, indented as the last
  declaration;

Two or more selectors, separated by comma:

```CSS
.foo,
.bar,
.baz {
    display: block;
    color: red;
    }
```

* each selector on its own new line;
* no empty lines between selectors;
* each selector in the list except the last one ends with a comma (`,`);
* no spaces between selector and comma (`,`);

You can group related properties indenting them by one (1) empty line:

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

No empty rulesets. This is wrong:

```CSS
.block {}
```

* one (1) empty line between rulesets related to the same block;
* indent entire related rulesets to signal their relation to one another,
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



<a id="selectors"></a>
## Selectors

* Universal selector (`\*`) is forbidden
* No cascade selectors
* _Exceptions_
* No selectors by ID
* No selectors by element
* _Exceptions_
* No selectors by attribute
* _Exceptions_
* the (`>`) selector better than (` `) space selector



<a id="values"></a>
## Property values

<a id="values_numbers"></a>
### Numbers
* No leading zero
* Maximum three (3) places after the point

<a id="values_colors"></a>
### Colors
* 6-character color dash notation with colors without transparency: `#44B1C3`
* 3-character color dash notation everywhere it's possible. For example `#F60`
instead of `#FF6600`
* Functional notation for colors with opacity different than 1:
`rgba( 34, 12, 64, 0.3)`
* Colors in the dash notation are upper cased

<a id="values_others"></a>
### Other
* values inside `url()` construction without quotes:

```CSS
.block {
    background-image: url(/img/sprite.svg);
    }
```

* no prefixed properties (it does Autoprefixer);
* no base64 encoded images (it does builder);
* no `!important` directive;
  * Except cases when you use it proactively. Proactive use of `!important`
    means that it's used as a guarantee that some rule always will work, but not
    as a fix of a specificity problem you’ve already encountered. For example:

    ```CSS
        .hidden {
            display: none !important;
        }
    ```

* no units for zero values: `margin: 0` is ok, but: `margin: 0px` is wrong;



<a id="bem"></a>
## BEM

We use [BEM methodology](https://en.bem.info/method/) and according class names.

<a id="bem_naming"></a>
### Naming conventions

*Class name:*
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


<a id="bem_block"></a>
### Block

```CSS
.block {
    /* declarations */
    }
```

for example:

```CSS
```


<a id="bem_element"></a>
### Element

```CSS
.block__element {
    /* declarations */
    }
```

for example:

```CSS
```


<a id="bem_modifier"></a>
### Modifier

```CSS
.block_modifier-name_modifier-value {
    /* declarations */
    }
```

for example:

```CSS
```



<a id="comments"></a>
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



<a id="media-queries"></a>
## Media queries

_TODO: describe how we're going to write media queries_



<!-- ## Global classes

* We have limited number of global classes which can be applied to any element.
The exhaustive list of these kind of classes listed below:
  * `.hidden`
  * `.invisible`
  * `.non-scrollable`
  * `.out-of-viewport` -->

<!-- ## Files structure

* Each block have to be stored in their own file named as the block
* Avoid using overflow: hidden; rule, especially to clear floats



## Tools

* Settings for more popular editors (PHP Storm, Sublime Text, Atom)
* Snippets
* Bookmark to browser -->
