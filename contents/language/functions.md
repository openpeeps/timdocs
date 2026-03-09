---
title: "Functions"
description: "Definition and usage of functions in Tim Engine"
keywords: ["functions", "tim engine", "definition", "usage", "documentation"]
---

## Function definition
Functions are reusable blocks of code that perform a specific task. They allow you to organize your code, avoid repetition, and make it more modular and maintainable. In **Tim Engine**, you can define functions using the `fn` or `func` keywords, followed by the function name, parameters, return type, and the function body. For example:
```
fn greet(name: string): string =
  return "Hello, " & $name & "!"

echo greet("Tim Engine")  // Output: Hello, Tim Engine!
```

## Function overloading
Tim Engine supports function overloading, which means you can define multiple functions with the same name but different parameter lists. The correct function will be called based on the arguments passed. For example:
```
fn greet(name: string, age: int): string =
  return "Hello, " & $name & "!" & " You are " & $age & " years old."
```

## Aliases
You can define functions using the `fn` or `func` keywords. For example:
```
fn greet(name: string): string =
  return "Hello, " & $name & "!"

// or, using the curly braces syntax
func greet(name: string): string {
  return "Hello, " & $name & "!"
}
```

## Mixing with HTML elements
**HTML elements cannot be defined inside a function body**. Trying to mix HTML elements inside a function body will result in a `CodeGenError`:
```
'HTML' can only be used inside a macro [CodeGenError]
```

Sure, you can return a string that contains HTML, and trick the engine into rendering it as HTML, **but that's for amateurs!**

<div class="alert alert-info rounded-4" role="alert">
  <div class="alert-content">
    For adding modularity to your templates and reusing components you should use <code>macros</code> instead. 😎 👉 Check <a href="/language/macros" class="alert-link">Macros</a> for more information.
  </div>
</div>