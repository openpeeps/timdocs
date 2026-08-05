---
title: "Imports & Includes"
description: "About modules, imports, includes, and code organization in Tim Engine."
keywords: ["modules", "imports", "tim engine", "code organization", "namespaces"]
---

Modules are a way to organize your code into separate files and namespaces. Like any other programming language, Tim Engine allows you to define modules and import them into other parts of your code. This helps you keep your codebase clean, modular, and maintainable.

## Importing local modules
To import a module in Tim Engine, you can use the `@import` statement followed by a stringified path to the module file. For example:
```
@import "utils"
@import "../some/other/utils"
```

## Standard library modules
Tim Engine comes with a [standard library](/libraries) that provides a wide range of built-in functions and modules for common tasks. You can import standard library modules using the `@import` statement with the module name. For example:
```
@import "std/json"
```

The following standard library modules are currently available:

- `std/system` — automatically imported into every template; provides the built-in operators and core functions
- `std/strings` — string manipulation functions
- `std/arrays` — array manipulation functions
- `std/objects` — object manipulation functions
- `std/json` — JSON parsing, serialization and utilities

The `system` module is always available without an explicit import. The math, times, email and FFI modules are planned but are not yet importable as standalone `std/...` modules.

## External packages
If you have installed external packages using the package manager, you can import modules from those packages as well. The syntax is the same as importing local modules, but you need to prefix the import path with the `pkg` keyword. For example:
```
@import "pkg/bootstrap/grid"
```

This will import the `grid` module from the `bootstrap` package. For more information on how to deal with packages, see the [package manager documentation](/package-manager).