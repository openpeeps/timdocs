---
title: "System Library"
description: "Documentation for the System Library in Tim Engine, which provides the essential operators, types, and functions for writing templates and scripts."
keywords: ["system library", "tim engine", "operating system", "system-level tasks", "math", "documentation"]
---

The `std/system` library in Tim Engine provides the standard functions, built-in operators (like `+`, `-`, `*`) and also comparison operators (like `==`, `!=`, `<`, `>`) that are essential for performing various operations in your templates and scripts. This library is **automatically imported into every template**, so you can use its functions and operators without needing to import it explicitly.

The math utilities (`abs`, `min`, `max`, `round`, `floor`, `ceil`, `sqrt`) are also part of the system library — there is no separate `std/math` module to import.

<div class="alert alert-info rounded-4" role="alert">
  <div class="alert-content">The standard library feature is not available in the Source-to-Source (S2S) mode. <strong>You must stick to the built-in operators and functions provided by the target language when using S2S mode.</strong></div>
</div>

### Operators
The system library registers the arithmetic, comparison, assignment and concatenation operators for `int`, `float`, `bool` and `json` values:

- Arithmetic: `+`, `-`, `*`, `/`
- Assignment: `+=`, `-=`, `*=`, `/=`
- Comparison: `==`, `!=`, `<`, `<=`, `>`, `>=`
- Logical: `not(x)`
- Identity: `is(a, b)`, `isnot(a, b)` — strict type-and-value comparison
- Concatenation: `&` — works with `string`, `int`, `float`, `bool` and `json` operands (e.g. `"Hello " & name`, `$count & " items"`)

### Type conversion

##### `toInt`
```
fn toInt(f: float): int
```
Convert a float to an integer.

##### `parseInt`
```
fn parseInt(s: string): int
```
Parse a string into an integer.

##### `toFloat`
```
fn toFloat(i: int): float
fn toFloat(i: json): float
```
Convert an integer or JSON number to a float.

##### `toBool`
```
fn toBool(x: int): bool
fn toBool(x: string): bool
fn toBool(x: json): bool
```
Convert a value to a boolean.

##### `toString`
```
fn toString(x: int): string
fn toString(x: float): string
fn toString(x: bool): string
fn toString(x: json): string
fn toString(x: object): string
```
Convert a value to its string representation. An object is converted to a JSON string.

##### `type`
```
fn type(x: any): string
```
Return the type name of a value as a string.

##### `jsonType`
```
fn jsonType(x: json): string
```
Return the type name of a JSON value.

##### `intVal` / `strVal`
```
fn intVal(x: json): int
fn strVal(x: json): string
```
Extract the integer or string value from a JSON value.

### Length and index helpers

##### `len`
```
fn len(x: string): int
fn len(x: json): int
fn len(x: array): int
```
Return the length of a string, JSON value or array.

##### `high`
```
fn high(x: json): int
fn high(x: array): int
```
Return the highest valid index of a JSON value or array (i.e. `len - 1`).

##### `inc` / `dec`
```
fn inc(i: int)
fn dec(i: int)
```
Increment or decrement an integer in place.

### Math functions

##### `abs`
```
fn abs(n: int): int
fn abs(n: float): float
```
Return the absolute value of `n`.

##### `min` / `max`
```
fn min(a: int, b: int): int
fn min(a: float, b: float): float
fn max(a: int, b: int): int
fn max(a: float, b: float): float
```
Return the smaller / larger of the two values.

##### `round` / `floor` / `ceil`
```
fn round(n: float): int
fn floor(n: float): int
fn ceil(n: float): int
```
Round `n` to the nearest integer, round down, or round up.

##### `sqrt`
```
fn sqrt(n: float): float
```
Return the square root of `n`.

### OS operations
The `std/system` library provides a minimal set of functions for performing various OS operations, such as reading and writing files, sleeping for a specified duration.

##### `readFile`
```
fn readFile(path: string): string
```
Read a file and return its content as a string.

##### `writeFile`
```
fn writeFile(path: string, content: string)
```
Write a file with the specified content.

##### `sleep`
```
fn sleep(ms: int)
```
Sleep for a specified duration (in milliseconds).

### JSON parsing
The `std/system` library also includes functions for parsing JSON data, which can be useful for working with APIs or configuration files.

##### `parseJSON`
```
fn parseJSON(content: string): json
```
Parse a JSON string and return it as a JSON value.

##### `loadJSON`
```
fn loadJSON(path: string): json
```
Load JSON data from a file and return it as a JSON value.

##### `remoteJSON`
```
fn remoteJSON(url: string): json
```
Load JSON data from a remote URL and return it as a JSON value. This function performs an HTTP GET request to the specified URL and parses the response as JSON.

##### `fetch`
```
fn fetch(url: string): json
fn fetch(url: string, options: json): json
```
Perform an HTTP request and return the response as JSON. The `options` object can carry request settings.

##### `hasKey`
```
fn hasKey(obj: json, key: string): bool
```
Check if a JSON object contains the given key.

### Random

##### `shuffle`
```
fn shuffle(arr: array): array
```
Return a new array with the elements in random order.

### Output

##### `echo`
```
fn echo(x: string | int | float | bool | json | nil | object | array | pointer)
```
Print a value to the standard output.

##### `assert`
```
fn assert(condition: bool)
```
Assert that a condition is true; raises an error if it is not.

### HTML escaping

##### `escape`
```
fn escape(s: string): string
```
Escape HTML special characters in `s` (`&`, `<`, `>`, `"`, `'`).

##### `unescape`
```
fn unescape(s: string): string
```
Decode HTML entities back into their original characters.
