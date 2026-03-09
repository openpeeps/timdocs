---
title: "Tim Syntax"
description: "This page covers the basics of Tim's syntax, including variables, control structures, and more."
---

Tim Engine's syntax is indentation-based, similar to **Nim**, **Ruby** or **Python**. This means that the structure of your code is determined by its indentation level, making it clean and easy to read. **Inspired by the Emmet syntax**, Tim allows you to create complex HTML structures with minimal code using a simple and intuitive syntax. 👌


## Quick Example
Here is a simple example of Tim syntax that generates a basic HTML structure using **Bootstrap 5** classes:
```
div.container > div.row > div.col-12
  h1.title: "Welcome to Tim Engine!"
  p.description: "Tim Engine is a powerful templating engine and scripting language for developers."
  a.btn.btn-primary.px-4 href="https://example.com": "Get Started"
```

## Syntax - Basics
- **Elements**: HTML elements are defined by their tag name, followed by optional classes and attributes. For example, `div.container` creates a `div` element with the class `container`.
- **Nesting**: Child elements are indented under their parent element. For example, the `h1` and `p` elements are nested inside the `div.col-12` element.
- **Text Content**: To add text content to an element, you can use a colon `:` followed by the text. For example, `h1.title: "Welcome to Tim Engine!"`.
- **Attributes**: You can add attributes to elements using the `attr=value` syntax. For example, `a.btn.btn-primary.px-4 href="https://example.com"`.
- **Shorthand for IDs**: You can use `#` to define an element's ID. For example, `div#main` creates a `div` element with the ID `main`.
- **Shorthand for Classes**: You can use `.` to define an element's class. For example, `div.container` creates a `div` element with the class `container`.
- **Sibling Elements**: You can use the `>` operator to create sibling elements or indent them to create child elements.

## The language
The scripting language is what makes Tim Engine truly powerful and unique. 💪 It allows you to add dynamic behavior to your webpage and generate content based on **conditions**, **loops**, and more.

Tim Engine features a **strongly-typed data model**, supporting primitive types like **strings**, **numbers**, **booleans**, as well as composite types such as **arrays** and **objects**. You can leverage built-in **functions** or define **custom functions** to efficiently manipulate data and generate dynamic content.
