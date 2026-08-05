---
title: "JSON"
description: "Work with JSON data in Tim Engine using the std/json library."
keywords: ["json", "tim engine", "serialization", "parsing", "json library", "documentation"]
---

The `std/json` library provides functions for serializing and working with JSON values in Tim Engine. JSON values are also produced by the [system library](/libraries/system) functions `parseJSON`, `loadJSON`, `remoteJSON` and `fetch`, and support arithmetic operators (`+`, `-`, `*`, `/`) as well as `==` / `!=` comparisons.

To use the library, import it explicitly:

```
@import "std/json"
```

##### `join`
```
fn join(s: json, sep: string = ", "): string
```
Join the elements of a JSON array of strings into a single string, separated by `sep`.

##### `keys`
```
fn keys(obj: json): json
```
Return an array of the object's property keys.

##### `values`
```
fn values(obj: json): json
```
Return an array of the object's property values.

##### `pretty`
```
fn pretty(obj: json): string
```
Return a pretty-printed (indented) representation of the JSON value.

##### `get`
```
fn get(obj: json, key: string, default: json): json
```
Return the value of `key` in the object, or `default` if the key does not exist.

## Examples

```
@import "std/json"

var data = parseJSON("{\"name\": \"Alice\", \"age\": 30}")
p: $data["name"]         // outputs "Alice"
echo keys($data)         // Output: ["name", "age"]
echo pretty($data)       // pretty-printed JSON
```
