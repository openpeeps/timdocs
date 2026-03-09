---
title: "Variables"
description: "Definition and usage of variables in Tim Engine, including how to declare, assign, and use variables in your templates and scripts."
keywords: ["variables", "tim engine", "declaration", "assignment", "usage", "documentation"]
---

## Mutable variables
You can define mutable variables using the `var` keyword. For example:
```
var name: string          // variable 'name' of type string
$name = "Tim Engine"      // assigning a value to the variable 'name'
```

## Immutable variables
You can define immutable variables using the `const` keyword. A constant requires an initializer and cannot be reassigned after its initial value is set. For example:
```
const version = "1.0.0"   // constant 'version' with a string value
```

## Calling variables
Due to the design of Tim Engine, and how it processes HTML elements, you can call a variable by prefixing it with a `$` symbol. For example, to display the value of the `name` variable, you can use:
```
p: $name
```