# CSS/LESS code style

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
6. [LESS](#less)
  1. [Variables](#less_variables)
  2. [Mixins](#less_mixins)
  3. [Nesting](#less_nesting)
  4. [Imports](#less_imports)


---

- Status of this document: **Draft**
- Author: Dmitriy Bogolyubov
- E-mail: dmitriy.bogolyubov@lazada.com

---

Please, feel free to share your own ideas, join discussions and make corrections
(especially in those parts of the document which have not been filled out yet).
If you have any objections please do not put them off, it will be much harder to
add any changes after this document status will be changed from **Draft** to
**Standard**.

Scrutinize each rule at the point of view your daily work:
- Will you be able to adhere it in your work?
- Will it be comfortable for you?
- Does it work for your team?

If you found a grammar mistake or would like to reformulate
something for better understanding let me know as well.

---

<a id="base"></a>
## Base requirements

* UTF-8 encoding without BOM;
* unix-style line endings;
* 80-characters line wide where possible;
* four (4) spaces indents, no tabs;
* no trailing spaces (empty lines must contain only the line feed symbol);
* lowercase only, except custom values in quotes, url's and HEX-values;
* single quotes;
* one (1) empty line at the end of files;



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
* the closing brace (`}`) on its own new line, indented as the selector
  it belongs to;

**Grouping selectors**

Two or more selectors in one ruleset have to be separated by comma:

```CSS
.foo,
.bar,
.baz {
    display: block;
    color: red;
}
```

* each selector on its own new line;
* no empty lines between grouped selectors;
* each selector in the list except the last one ends with a comma (`,`);
* no spaces between selector and comma (`,`);

**Grouping properties**

You can group related properties adding one (1) empty line between groups of
properties:

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

This record will be wrong because grouped properties are not related to each
other:

```CSS
.block {
    display: block;

    font-size: 30px;
    background: #EEE;
}
```

**Empty rulesets**

Empty rulesets are not allowed. A ruleset is considered as empty if it doesn't
contain at least one styling rule. These record will be wrong:

```CSS
.block {}

.comment-inside {
    /*
        Still empty because comments are not the styling rules
    */
}
```

The only exception is if a block doesn't have any styling rules, but its
elements have, you can keep the block ruleset empty:

```CSS
.block {}

.block__element1 {
    background: #F00;
}

.block__element2 {
    background: #0F0;
}
```



<a id="selectors"></a>
## Selectors

Keep selectors as short as possible, in order to keep specificity down and
performance up.

**Universal selector (`*`) is forbidden**

```CSS
/* Wrong: */

* {
    box-sizing: border-box;
}
```

*Reasons:*

* with high probability it will change rules that you were not going
  to change;
* because browsers read selectors right-to-left, the rightmost selector is often
  critical in defining a selector’s performance;

**No selectors by ID**

```CSS
/* Wrong: */

#main {
    color: #F00;
}
```

*Reasons:*

* selectors by id give too much weight for the rules under it;
* it is impossible to use such blocks on the page more than one times;

**No selectors by element**

```CSS
/* Wrong: */

p {
    margin: 1em 0;
}

.block img {
    border: 1px solid #000;
}
```
*Reasons:*

* because with high probability the rules will be applied to elements you were
  not going apply to;
* inability to replace one tag on another without changing styles;

*Exceptions:*

* allowed to use in the reset/normalize styles files, which set basic
  styles for the whole project;
* allowed to use for styling selectors related to tables;
* allowed to use for styling embedded a third-party widgets;

**No selectors by attribute**

```CSS
/* Wrong: */

.input[type="text"] {
    font-size: 1em;
}

.input[disabled] {
    opacity: .5;
}


/* Right: */

.input_type_text {
    font-size: 1em;
}

.input_state_disabled {
    opacity: .5;
}
```

*Reasons:*

* attribute selectors has the same specificity as class selectors which
  leads to an increase in the specificity and complexity of the redefinition of
  the rules;

*Exceptions:*

* in case we need to style embedded a third-party widgets we have no ability to
  edit its markup we can use this approach:

```CSS
[id="third-party-widget"] {}
```


**No cascade selectors**

*Reasons:*

- the cascade increases specificity and limits the ability to extend
  and manipulate a codebase;

*Exceptions:*

- it's allowed to use a cascade if a block has a few themes and you need to add
specific styles to the block elements, based on a theme. For example:

```CSS
.box {
    background: #FFF;
}

.box__title {
    color: #000;
}

.box_theme_dark {
    background: #000;
}

.box_theme_dark > .box__title {
    color: #FFF;
}
```

*How to use:*

- use no more than two class selectors at once;
- prefer to use `A > E` selector instead of `A E` (space);



<a id="values"></a>
## Property values

<a id="values_numbers"></a>
### Numbers
* No leading zero. `.3` instead of `0.3`;
* Maximum three (3) places after the point. `2.345em` is ok, but `2.3456` is
  wrong;

<a id="values_colors"></a>
### Colors
* 6-character color hash notation for color calues without transparency:
  `#44B1C3`;
* 3-character color hash notation everywhere it is possible. For example `#F60`
  instead of `#FF6600`;
* functional notation for colors with opacity different than one (1):
  `rgba(34, 12, 64, .3)`;
* colors in the hash notation are uppercased: `#44B1C3`. Not: `#44b1c3`;

<a id="values_others"></a>
### Other
* values inside `url()` construction without quotes:

```CSS
.block {
    background-image: url(/img/sprite.svg);
}
```

* no prefixed properties (it does Autoprefixer);
  * except non-standard vendor properties like `webkit-tap-highlight-color`
  which is missing in the ["Can I Use"](http://caniuse.com) database. Please,
  remember that you have to have very good reasons to use it, so if there is
  a way to accomplish a task without such prefixed properties, do it.
* no base64 encoded images (it does a builder);
* no `!important` directive;
  * except cases when you use it proactively. Proactive use of `!important`
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

Describing the essence of BEM methodology is beyond the scope of
this document, everything you need you can find on the official BEM site:
[BEM methodology](https://en.bem.info/method/). Here are just described the
formal rules of naming CSS classes.

<a id="bem_naming"></a>
### Naming conventions

Class name:

* minimum 3 symbols length;
* always starts with a letter;
* allowed characters: letters `(a-z)`, digits `(0-9)`, underscore `(_)`,
  hyphen `(-)`;
* hyphen `(-)` to separate words;
* meaningful class names in English;
* no word contractions:

```CSS
/* Bad choice — contractions */
.lnk, .itm, .idx, .arr {}

/* Good choice */
.link, .item, .index, .arrow {}
```

* no abbreviations:

```CSS
/* Bad choice — abbreviations */
.pdp, .fb, .pm {}

/* Good choice */
.product-page, .facebook, .panel-menu {}
```

* strive to use place-independent names. For example, instead of a class like
`.site-nav`, choose something like `.primary-nav`; rather than
`.footer-links`, favour a class like `.sub-links`.
* no class names which describe block appearance, like `.blue` or `.border`.
Instead, favour a class like `.highlight-color`.


<a id="bem_block"></a>
### Block

Block is a common CSS class which has to meet common naming conventions,
described above. The only exception: underscore `(_)` cannot be used in the
block class name.

```CSS
.block {
    /* declarations */
}
```

for example:

```CSS
.button {
    display: inline-block;
    padding: 1em;
    background: #587185;
    color: #FFF;
}
```


<a id="bem_element"></a>
### Element

The element class name has the following structure:

1. the name of the block which owns the element;
2. two (2) underscore signs `(__)` following the block name;
3. the element name;

```CSS
.block__element {
    /* declarations */
}
```

for example:

```CSS
/* this is a block */
.button {
    ...
}

/* this is an element which belongs to the block */
.button__icon {
    display: inline-block;
    margin-right: 5px;
}
```

<a id="bem_modifier"></a>
### Modifier

The modifier may refer to an element or block and may be two types:

1. Boolean
2. Key-Value


#### Boolean modifiers

Boolean modifiers represent a state of a block/element and works like a flag
which can be set or unset. The full name is created using the scheme:

```
block-name_mod-name
```

1. a block or an element class name;
2. one (1) underscore sign `(_)`;
3. the name of the modifier;

Examples:

```CSS
/* Boolean block modifiers */
.input_disabled {}
.tabs_rearrangeable {}

/* Boolean element modifiers */
.menu__list-item_dynamic {}
.form__message_emphasized {}
```


#### Key-Value modifiers

Key-values modifiers are used when the modifier can take more than two values
(set/unset). Good examples are:

```CSS
/* Placement*/
.dropdown_placement_top {}
.dropdown_placement_right {}
.dropdown_placement_bottom {}
.dropdown_placement_left {}

/* Theme */
.header_theme_light {}
.header_theme_dark {}
.header_theme_solarized {}
```

The full name is created using the scheme:

```
block-name_mod-name_mod-value
```

1. a block or an element class name;
2. one (1) underscore sign `(_)`;
3. the name of the modifier key;
4. one (1) underscore sign `(_)`;
5. the modifier value;

Examples:

```CSS
/* Key-Value block modifiers */
.popup_theme_dark {}
.button_size_m {}

/* Key-Value element modifiers */
.menu__item_type_radio {}
.dropdown_placement_top {}
```



<a id="less"></a>
## LESS

LESS-files must be treated as CSS ones, but with additional rules described
below.

The list of features we use with preprocessor is limited three key features:

1. Variables
2. Mixins
3. Nesting
4. Imports

Using the other features is forbidden because on the one hand it leads to
excessive complexity and on the other hand do not offer any significant benefits
which could help to write and mantain code easier.

<a id="less_variables"></a>
### Variables

* declare variables only at the top of the file before all rulesets, but after
import declarations (if there are);
* two (2) empty lines between the last declared variable and the first ruleset;
* each variable declaration starts on its own new line;
* no empty lines between variable declarations;
* no spaces at the start of the line before the variable name;
* no spaces between variable name and colon (`:`);
* one (1) space between colon (`:`) and value;
* each declaration ends with a semicolon (`;`);
* no spaces between the value and the semicolon (`;`);
* use variables only as property values;
* variable name:
  * minimum three (3), maximum 20 symbols length;
  * always starts with a letter;
  * allowed characters: letters `(a-z)` and digits `(0-9)`;
  * camelCase;

Example of right usage:

```LESS
@linkColor: #AAA;
@linkColorHover: #555;


.link {
    color: @linkColor;
}

.icon {
    background: url(@{images}/white-sand.png);
}
```

These are considered as wrong usage:

```LESS
// WRONG! Using a variable value not as a property value
.@{my-selector} {
    margin: 0 auto;
}


```


<a id="less_mixins"></a>
### Mixins

It is forbidden to use mixins for prefixed properties, it automatically does
Autoprefixer.


<a id="less_nesting"></a>
### Nesting

Avoid unnecessary nesting. Just because you can nest, doesn't mean you always should. Consider nesting only if you must scope styles to a parent and if there are multiple elements to be nested.

We are using nesting for:

* constructing BEM classes:

```CSS
.menu {
    &__item {
        ...
        &_state_active {

        }
    }
}
```

* the cascade:

```CSS
table > thead > tr {
    > th {
        ...
    }
    > td {
        ...
    }
}
```

* pseudo-classes:

```CSS
.button {
    &:hover,
    &:focus {
        ...
    }

    &:active {
        ...
    }
}
```

We don't use nesting:

* if all rules except the last one are empty
* this way:

```CSS
.child {
    .parent & {
        ...
    }
}
```


<a id="less_imports"></a>
### Imports

* declare imports only at the top of the file before all rulesets;
* two (2) empty lines between the last import declaration and the first ruleset;
* each import statement starts on its own new line;
