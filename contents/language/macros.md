---
title: "Macros and Components"
description: "Documentation for macros in Tim Engine, which are reusable templates that can generate HTML elements and can be used to create components in your templates."
keywords: ["macros", "components", "tim engine", "reusable templates", "documentation"]
---

## What are macros?
Macros in Tim Engine can be used to create reusable components, elements or templates. Macros are pretty similar to functions, but they are designed specifically for generating HTML and **returning HTML elements**.

## Defining and using macros
Here is an example of a simple macro that generates a button component:
```
macro PrimaryButton(label: string, url: string):
  a.btn.btn-primary title=$label href=url: $label
```

Calling a macro implies prefixing it with a `@` symbol. For example, to use the `Button` macro we defined above, you can do:
```
@PrimaryButton("Click Me", "https://example.com")
```

Another example, this time with a more complex macro that generates a card component:
```
macro Card(title: string, content: string):
  div.card
    div.card-header: $title
    div.card-body: $content
```

```
for $i in 1..3:
  @Card("Card " & $i, "This is the content of card " & $i)
```

As you can see, macros allow you abstract away complex HTML structures and reuse them throughout your templates, making your code cleaner and more maintainable.