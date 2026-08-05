---
title: "Standard Libraries"
description: "An overview of the standard libraries included with Tim Engine."
keywords: ["standard library", "stdlib", "tim engine", "built-in modules", "libraries"]
---

Thanks to [VanCode's modular design](https://github.com/openpeeps/vancode), the standard library of Tim Engine offers a wide range of FFI modules and built-in functions that you can use in your projects. These libraries cover various domains such as math, string manipulation, file I/O, and more.

The following standard library modules are available:

- `std/system` — automatically imported into every template; provides the built-in operators, type conversions, math utilities, OS operations, JSON parsing and more
- `std/strings` — string manipulation functions
- `std/arrays` — array manipulation functions
- `std/objects` — object manipulation functions
- `std/json` — JSON serialization and utilities

<div class="row g-3">
  <div class="col-md-6">
    <div class="card rounded-4 p-4">
      <h6 class="mt-0 mb-2">System library</h6>
      <p class="small mb-0 lh-sm">System module provides the basics, types and functions for the engine to work, including math and JSON utilities.</p>
    </div>
  </div>
  <div class="col-md-6">
    <div class="card rounded-4 p-4">
      <h6 class="mt-0 mb-2">Strings</h6>
      <p class="small mb-0 lh-sm">String manipulation functions, including formatting, splitting, and more.</p>
    </div>
  </div>
  <div class="col-md-6">
    <div class="card rounded-4 p-4">
      <h6 class="mt-0 mb-2">Arrays</h6>
      <p class="small mb-0 lh-sm">Array manipulation functions, including creation, resizing, and more.</p>
    </div>
  </div>
  <div class="col-md-6">
    <div class="card rounded-4 p-4">
      <h6 class="mt-0 mb-2">Objects</h6>
      <p class="small mb-0 lh-sm">Object manipulation functions, including creation, property access, and more.</p>
    </div>
  </div>
  <div class="col-md-6">
    <div class="card rounded-4 p-4">
      <h6 class="mt-0 mb-2">JSON</h6>
      <p class="small mb-0 lh-sm">JSON serialization and utilities, including parsing, pretty-printing, keys and values access.</p>
    </div>
  </div>
</div>