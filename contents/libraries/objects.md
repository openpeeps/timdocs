---
title: "Objects"
description: "Details about objects in Tim Engine, including how to create and manipulate objects in your templates and scripts."
keywords: ["objects", "tim engine", "creation", "manipulation", "documentation"]
---

Objects in Tim Engine are a fundamental data structure that allows you to store
and manipulate data in a structured way. The `std/objects` library provides functions for creating and working with objects in your templates and scripts.

## Creating Objects
You can create an object using the curly braces `{}` syntax, just like in many other programming languages (e.g., JavaScript). For example:
```
var person = {
  name: "Alice",
  age: 30,
  isStudent: false
}
```

In this example, we create an object `person` with three properties: `name`, `age`, and `isStudent`. Each property has a corresponding value


### Accessing Object Properties
You can access the properties of an object using dot notation. For example:
```
p: $person.name       // outputs "Alice"
p: $person.age        // outputs 30
p: $person.isStudent  // outputs false
```

### Modifying Object Properties
> [!NOTE]
> Mutating an object's properties in place (`$person.name = "Bob"`) is not yet supported. Construct a new object if you need a modified copy.

### Nested Objects
Objects can also contain other objects as properties, allowing you to create complex data structures. For example:
```
var company = {
  name: "Tech Corp",
  employees: {
    alice: {
      age: 30,
      position: "Developer"
    },
    bob: {
      age: 25,
      position: "Designer"
    }
  }
}
```

### Nested Arrays
Objects can also contain arrays as properties, which can be useful for storing lists of data. For example:
```
var team = {
  name: "Development Team",
  members: [
    { name: "Alice", role: "Developer" },
    { name: "Bob", role: "Designer" },
    { name: "Charlie", role: "Project Manager" }
  ]
}
```

<div class="alert alert-info rounded-4" role="alert">
  <div class="alert-content">For more infos about arrays, check the <a href="/libraries/arrays">Arrays library documentation</a>, where you can find all the functions and utilities for working with arrays in Tim Engine.</div>
</div>


### Iterating Over Object Properties
You can inspect an object's properties using the `keys` and `values` functions from the `std/objects` library:

```
@import "std/objects"

var person = { name: "Alice", age: 30 }
echo keys($person)    // Output: ["name", "age"]
echo values($person)  // Output: ["Alice", 30]
```

> [!NOTE]
> Iterating over an object's key/value pairs directly (`for $key, $value in $person`) is not yet supported.

## The Library
The `std/objects` library provides functions for working with objects in your templates and scripts:

##### `hasKey`
```
fn hasKey(obj: object, key: string): bool
```
Check if the object contains the given property key.

##### `len`
```
fn len(obj: object): int
```
Return the number of properties in the object.

##### `isEmpty`
```
fn isEmpty(obj: object): bool
```
Check if the object has no properties.

##### `clear`
```
fn clear(obj: object)
```
Remove all properties from the object. The object is modified in place.

##### `keys`
```
fn keys(obj: object): array
```
Return an array of the object's property keys.

##### `values`
```
fn values(obj: object): array
```
Return an array of the object's property values.

> [!NOTE]
> The `std/objects` library also exposes `add`, `delete`, `insert`, `find` and `join` with the same signatures as their `std/arrays` counterparts, operating on object-backed collections.
