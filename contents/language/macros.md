---
title: "Macros and Components"
description: "Reusable templates that can generate HTML elements and can be used to create components in your templates."
keywords: ["macros", "components", "tim engine", "reusable templates", "documentation"]
---

## What are macros?
Macros in Tim Engine can be used to create reusable components, elements or templates. Macros are pretty similar to functions, but they are designed specifically for generating HTML and **returning HTML elements**.

## Defining and using macros
Here is an example of a simple macro that generates a button component:
```
macro PrimaryButton(label: string, url: string) =
  a.btn.btn-primary href=$url: $label
```

Calling a macro implies prefixing it with a `@` symbol. For example, to use the `PrimaryButton` macro we defined above, you can do:
```
@PrimaryButton("Click Me", "https://example.com")
```

Another example, this time with a more complex macro that generates a card component:
```
macro Card(title: string, content: string) =
  div.card
    div.card-header: $title
    div.card-body: $content
```

```
for $i in 1..3:
  @Card("Card " & $i, "This is the content of card " & $i)
```

As you can see, macros allow you abstract away complex HTML structures and reuse them throughout your templates, making your code cleaner and more maintainable.

## Macro with trailing statements
Macros accept trailing statements, which allows you to pass a block of code to the macro. This is useful for creating more flexible components that can accept **varying content**. Here's an example of a macro that generates a Bootstrap column and accepts trailing statements for the content:
```
macro col(width: int) =
  div.col class="col-lg-" & $width:
    @statement
```

Calling this macro with trailing statements would look like this:
```
@col(6):
  p: "This is some content inside the column."
```

This will generate a Bootstrap column with the specified width and the content:
```html
<div class="col col-lg-6">
  <p>This is some content inside the column.</p>
</div>
```

`@statement` is a special inner macro that represents the block of code passed as trailing statements. When the macro is called, the block of code following the macro call is passed to `@statement`, which can then be used within the macro to generate the desired HTML structure.


Calling the `col` macro without trailing statements will simply generate an empty column:
```
@col(6)
```

the inner `@statement` won't have any content to render, so the generated HTML will be:
```html
<div class="col col-lg-6"></div>
```

> [!NOTE]
> When referencing macro parameters inside attributes or class names, interpolate them with the `$` prefix (e.g. `class="col-lg-" & $width` or `title=$label`).