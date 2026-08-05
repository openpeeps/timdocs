---
title: "Tim Syntax"
description: "This page covers the basics of Tim's syntax, including variables, control structures, and more."
---

Tim Engine's syntax is indentation-based, similar to **Nim**, **Ruby** or **Python**. This means that the structure of your code is determined by its indentation level, making it clean and easy to read. **Inspired by the Emmet syntax**, Tim allows you to create complex HTML structures with minimal code using a simple and intuitive syntax. 👌


## Quick Example
Here is a simple example of Tim syntax for a basic HTML structure using **Bootstrap 5**:
```
div.container > div.row > div.col-12
  h1.display-4.fw-bold: "Welcome to Tim Engine!"
  p.lead: "Tim Engine is a powerful templating engine and scripting language for developers."
  a.btn.btn-primary.px-4.rounded-3
    href="https://example.com": "Get Started"
```

## Syntax - Basics
- **Elements**: HTML elements are defined by their tag name, followed by optional classes and attributes. For example, `div.container` creates a `div` element with the class `container`.
- **Nesting**: Child elements are indented under their parent element. For example, the `h1` and `p` elements are nested inside the `div.col-12` element.
- **Text Content**: To add text content to an element, you can use a colon `:` followed by the text. For example, `h1.title: "Welcome to Tim Engine!"`.
- **Attributes**: You can add attributes to elements using the `attr=value` syntax. For example, `href="https://example.com"`.
- **Shorthand for IDs**: You can use `#` to define an element's ID. For example, `div#main` creates a `div` element with the ID `main`.
- **Shorthand for Classes**: You can use `.` to define an element's class. For example, `div.container` creates a `div` element with the class `container`.
- **Sibling Elements**: You can use the `>` operator to create sibling elements or indent them to create child elements.

### Element multiplication
The `tag*N` syntax repeats an HTML element `N` times and injects a 0-based `$i` index variable you can use inside the element:
```
li*3: "Item"
```
```
ul
  li*3: $items[$i]
```
This produces three `<li>` elements. Inside the repeated element, `$i` holds the current repetition index (0, 1, 2, ...).

### Input type shorthand
For `<input>` elements, the colon shorthand is used to set the `type` attribute when there is no whitespace before the colon:
```
input:time
input:color
input:range
```
This produces `<input type="time">`, `<input type="color">` and `<input type="range">`. Subsequent `.class` / `#id` attributes still apply.

### SVG
`svg` elements automatically get an `xmlns="http://www.w3.org/2000/svg"` attribute at parse time. This is skipped if you provide your own `xmlns`.

## The language
Tim engine is a Domain-Specific Language (DSL), it is designed to be used for creating HTML templates, Tim includes a powerful scripting language that allows you to add the dynamic behaviour to your templates and generate content based on conditions, loops, and more.

Tim Engine features a **strongly-typed data model**, supporting primitive types like **strings**, **numbers**, **booleans**, as well as composite types such as **arrays** and **objects**. You can leverage built-in **functions** or define **custom functions** to efficiently manipulate data and generate dynamic content.

### Data Types & Literals

| Type | Example |
|---|---|
| `string` | `"hello"`, `'hello'`, `"""raw"""` |
| `int` | `42`, `-5` |
| `float` | `3.14`, `-0.5` |
| `bool` | `true`, `false` |
| `nil` | `nil` |
| `array` | `[1, 2, 3]` |
| `object` | `{name: "Alice", age: 30}` |

### String variants
- **Double-quoted** `"..."` — escape sequences (`\n`, `\r`, `\t`, `\"`, `\\`, `\0`), multi-line allowed
- **Single-quoted** `'...'` — single-line only, no escape processing
- **Triple-quoted** `"""..."""` — raw text, no escaping needed, multi-line


### Reserved keywords
```
if, elif, else, for, while, in, and, or, var, const,
fn, func, macro, iterator, return, yield, break,
echo, type, object, nil, true, false
```

> [!NOTE]
> `case`, `of`, `discard` and `continue` are recognized by the lexer but are **not yet implemented** in the engine. Backtick string literals (`` `...` ``) are also recognized by the lexer but not yet implemented.

### Operators & Precedence (highest first)

| Prec | Operators | Assoc |
|---|---|---|
| 45 | `.` (dot access) | Left |
| 40 | `[` (bracket access) | Left |
| 20 | `*`, `/` | Left |
| 10 | `+`, `-` | Left |
| 6 | `&` (concat) | Left |
| 5 | `==`, `!=`, `>`, `<`, `>=`, `<=` | Left |
| 3 | `and`, `&&` | Left |
| 2 | `or`, `\|\|` | Left |
| 1 | `=` (assignment) | Right |

Range `..` is parsed as an iterator call. Equality/identity helpers `is(a, b)` and `isnot(a, b)` are available as standard library functions (see the [System library](/libraries/system)).


### Comments

#### Single-line `//`
```
// This is a comment
div.container  // inline comment
```

#### Block `/* */`
```
/*
  Documentation comment
  Transpiled to HTML <!-- comment -->
*/
```

### Directives

#### `@javascript` / `@css` — with minification
```
@javascript
  console.log("Hello, World!")
@end

@css
  body { color: red; }
@end
```

#### `@html` — raw HTML (no escaping)
```
@html
  <custom>raw html here</custom>
@end
```

#### `@client` — SPA-aware block
```
@client
  // client-side only content
@end
```

#### `@static` — compile-time evaluator
The `@static` block is a compile-time evaluator for `for` loops and `if`/`elif`/`else` conditionals. The body is captured, `{$varName}` / `$varName` patterns are substituted with literal iteration values, and the result is re-parsed and inlined into the parent AST at compile time:
```
@static for $x in ["a", "b", "c"]:
  p: "Value: {$x}"
```
```
@static for $i in 1..3:
  p: "Item $i"
```
```
@static if true:
  div.yes
else:
  div.no
```

> [!NOTE]
> `@static if` conditions currently support literal boolean values; comparison expressions in the condition are not yet evaluated. `@static for` supports literal arrays and integer ranges (`start..end`).

#### `@LitElement` — custom elements
`@LitElement, ClassName` defines a Lit-style custom HTML element. The tag name is derived from the class name (converted to kebab-case). The body supports `@javascript` blocks (concatenated into the class body) and a single `@client` block (the render template):
```
@LitElement, MyButton
  @javascript
    static get properties() { return { label: String }; }
  @end
  @client
    button.btn: $this.label
```

This generates a JavaScript class extending `LitElement` with `connectedCallback`, `render()`, and a `customElements.define('my-button', MyButton)` call. Client-side only; server-side rendering emits the class as a `<script>` block.

#### `@view` — layout placeholder
```
body
  div.container
    @view
```