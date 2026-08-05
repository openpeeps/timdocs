---
title: "Arrays"
description: "Learn about arrays in Tim Engine, including how to create, manipulate, and use arrays in your templates and scripts."
keywords: ["arrays", "tim engine", "creation", "storage", "manipulation", "documentation"]
---

Arrays in Tim Engine represents a collection of values that can be of any type, including other arrays or objects. The `std/arrays` library provides functions for creating and working with arrays in your templates and scripts.

## Creating arrays
You can create an array using the `[]` syntax. For example:
```
var fruits = ["apple", "banana", "cherry"]
```

## Accessing array elements
You can access individual elements of an array using their index, which starts at 0. For example:
```
echo fruits[0]  // Output: apple
echo fruits[1]  // Output: banana
```

## The Library
The `std/arrays` library provides various functions for manipulating arrays, such as adding, removing, and sorting elements. Here is the list of available functions in the `std/arrays` library:

##### `add`
```
fn add(s: array, item: any)
```
Append a new item to the end of an array. The array is modified in place.

##### `insert`
```
fn insert(s: array, item: any, offset: int)
```
Insert an item into an array at a specific index. The array is modified in place.

##### `delete`
```
fn delete(s: array, offset: int)
```
Delete an item from an array at a specific index. The array is modified in place.

##### `contains`
```
fn contains(arr: array, x: string): bool
```
Check if an array contains a specific value.

##### `find`
```
fn find(s: array, item: any): int
```
Return the index of the first occurrence of `item` in the array, or `-1` if it is not found.

##### `join`
```
fn join(s: array): string
```
Join the elements of an array of strings into a single string, separated by `", "`.

##### `dedup`
```
fn dedup(s: array)
```
Remove duplicate values from an array (by value). The array is modified in place.

##### `isEmpty`
```
fn isEmpty(arr: array): bool
```
Check if the array has no elements.

##### `first`
```
fn first(arr: array): any
```
Return the first element of the array.

##### `last`
```
fn last(arr: array): any
```
Return the last element of the array.

##### `reverse`
```
fn reverse(arr: array): array
```
Return a new array with the elements in reversed order.
