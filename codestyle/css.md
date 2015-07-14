# CSS Styleguide

## Base principles

* Modular
* Independent blocks
* 80-characters column
* 4 spaces indents, no tabs
* No cascade
* No selectors by ID
* No selectors by element (* there are limited cases when we can use selectors by ID)
* No !important rules (* there are limited cases when we can use the !important rule)
* Predominantly you should avoid using selectors by attribute, but there are limited cases when it can be useful
* Single quotes
* Don’t put two or more blocks/elements on one node (except global classes)
* No spaces after the end of lines. Empty line must contain only carriage return symbol.
* UTF-8 encoding
* Unix-style line endings
* One (1) empty line at the end of each file
* Avoid using overflow: hidden; rule, especially to clear floats

## Naming conventions

* Lowercase only
* Use hyphen (-) to separate words. Camel case and underscores are not used for regular classes
* Don’t use prefixes for class names
* Use BEM methodology
* The naming convention follows this pattern:
```
.block {
		…
		}
.block__element {
		…
		}
.block_modifier-name_modifier-value {
		…
		}
```
* .block represents the higher level of an abstraction or component
* .block__element represents a descendent of .block that helps form .block as a whole
* .block—modifier represents a different state or version of .block or element
* JS-Lazada-* is reserved


## Naming

* Strive to use place-independent names. For example, instead of a class like .site-nav, choose something like .primary-nav; rather than .footer-links, favour a class like .sub-links.
* Avoid using class names which describe block appearance, like .blue or .border. Instead, favour a class like .highlight-color

## Indents

* Meaningful whitespace:
** 
* Indent entire related rulesets to signal their relation to one another, for example:
```
.foo {
		…
		}
		.foo__bar {
				…
				}
				.foo__baz {
						…
						}
```

## Comments

* Begin every new major section of a CSS project with a title:
```
/*——————————————————*\
    #SECTION-TITLE
\*——————————————————*/

.selector {}
```

## Ruleset

* The standard ruleset looks like:
```
[selector] {
		[property]: [value];
		[<—declaration—>]
		}
```
** Each ruleset starts from a new line
** At first a selector follows
** The opening brace ({) on the same line as our last selector;
** A space before our opening brace ({);
** Each declaration on its own new line
** Each declaration indented by four (4) spaces
** Properties and values on the same line
** Each rule starts from a property name, then follows a colon, one (1) space and a property value
** Each declaration ends with semicolon
** Each ruleset ends with the closing brace (}) on its own new line, indented as the last declaration in the list
* We can combine two or more selectors with a comma like this:
```
.foo,
.bar,
.baz {
		display: block;
		color: red;
		…
		}
```
** Each selector starts from a new line
** Each selector in a list except the last ends with a comma
* You can combine related properties in ruleset and split them from the others by one space line:
```
.foo {
		position: absolute;

		border-style: solid;
		border-width: 1px 0 0 1px;
		border-color: #FFF;
		
		background-color: #000;
		background-position: left top;
		}
```
* Use one of these two ways to define a color:
```
.foo {
		color: #44B1C3;
		}
```
or this one, if you need to define an opacity:
```
.foo {
		background-color: rgba(215, 40, 40, 0.9);
		}
```
* HEX colors are always written in upper case:
```
.foo {
		color: #44B1C3;
		}
```
* Use shorthand HEX notation abbreviates 6-character RRGGBB CSS colors into 3-character RGB shorthand. So instead of this:
```
.foo {
		color: #FF6600;
		}
```
write this:
```
.foo {
		color: #F60;
		}
```
* Rulesets related to the same block follow one each other without space lines or other separators
* Values inside url() construction without quotes:
```
.foo {
		background-image: url(/img/sprite.svg);
		}
```
* We don’t use prefixed properties (it does Autoprefixer)

## Global classes

* We have limited number of global classes which can be applied to any element. The exhaustive list of these kind of classes listed below:
** .hidden
** .invisible
** .non-scrollable
** .out-of-viewport

## Media queries

## Files structure

* Each block have to be stored in their own file named as the block

## Recommendations

* The “>” selector better than “ “ (space) selector

## Tools

* Settings for more popular editors (PHP Storm, Sublime Text, Atom)
* Snippets
* Bookmark to browser
