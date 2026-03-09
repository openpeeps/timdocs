---
title: "System Library"
description: "Documentation for the System Library in Tim Engine, which provides essential functions for interacting with the operating system and performing system-level tasks."
keywords: ["system library", "tim engine", "operating system", "system-level tasks", "documentation"]
---

## Introduction
The `std/system` library in Tim Engine provides the standard functions, built-in operators (like `+`, `-`, `*`) and also comparison operators (like `==`, `!=`, `<`, `>`) that are essential for performing various operations in your templates and scripts. This library is automatically imported into every template, so you can use its functions and operators without needing to import it explicitly.


<div class="alert alert-info rounded-4" role="alert">
  <div class="alert-content">The standard library feature is not available in the Source-to-Source (S2S) mode. <strong>You must stick to the built-in operators and functions provided by the target language when using S2S mode.</strong></div>
</div>


### OS operations
The `std/system` library provides a minimal set of functions for performing various OS operations, such as reading and writing files, sleeping for a specified duration

```
fn writeFile*(path: string, content: string)
fn readFile*(path: string): string
fn sleep*(duration: int)
```

### JSON parsing
The `std/system` library also includes functions for parsing JSON data, which can be useful for working with APIs or configuration files.

```
fn parseJson*(content: string): json
fn loadJson*(path: string): json
fn remoteJson*(url: string): json
```