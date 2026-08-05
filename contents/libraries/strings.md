---
title: "Strings"
description: "Manipulate strings in Tim Engine, including concatenation, interpolation, and common string utilities."
keywords: ["strings", "tim engine", "concatenation", "interpolation", "utilities", "documentation"]
---

Here we list the functions provided by the `std/strings` library for manipulating strings in Tim Engine. These functions allow you to perform common string operations such as concatenation, interpolation, and various utilities for working with strings.

##### `contains`
```
fn contains(s: string, sub: string): bool
```
Check if the string `s` contains the substring `sub`. This function returns `true` if `sub` is found within `s`, and `false` otherwise.

##### `startsWith`
```
fn startsWith(s: string, prefix: string): bool
```
Check if the string `s` starts with the specified `prefix`. This function returns `true` if `s` begins with `prefix`, and `false` otherwise.

##### `endsWith`
```
fn endsWith(s: string, suffix: string): bool
```
Check if the string `s` ends with the specified `suffix`. This function returns `true` if `s` ends with `suffix`, and `false` otherwise.

##### `toUpper`
```
fn toUpper(s: string): string
```
Convert the string `s` to uppercase. This function returns a new string with all characters in `s` converted to uppercase.

##### `toLower`
```
fn toLower(s: string): string
```
Convert the string `s` to lowercase. This function returns a new string with all characters in `s` converted to lowercase.

##### `strip`
```
fn strip(s: string): string
```
Strip leading and trailing whitespace from the string `s`.

##### `split`
```
fn split(s: string, sep: string): array
```
Split the string `s` by the separator `sep` and return an array of substrings.

##### `replace`
```
fn replace(s: string, from: string, to: string): string
```
Replace all occurrences of `from` with `to` in the string `s`.

##### `repeat`
```
fn repeat(s: string, n: int): string
```
Return a new string consisting of `n` repetitions of the string `s`.

##### `capitalize`
```
fn capitalize(s: string): string
```
Return a copy of the string `s` with its first character converted to uppercase.

##### `count`
```
fn count(s: string, sub: string): int
```
Count the number of non-overlapping occurrences of `sub` in the string `s`.

##### `isAlphaNumeric`
```
fn isAlphaNumeric(s: string): bool
```
Check if all characters in the string `s` are alphanumeric.

##### `isDigit`
```
fn isDigit(s: string): bool
```
Check if all characters in the string `s` are digits.

#### Base64 Encoding and Decoding
The `std/strings` library also provides functions for encoding and decoding strings in Base64 format, which can be useful for encoding binary data or transmitting data in a text-based format.

##### `encode`
```
fn encode(s: string): string
```
Encode the string `s` in Base64 format. This function takes a string as input and returns a new string that is the Base64-encoded representation of the input string.

##### `decode`
```
fn decode(s: string): string
```
Decode a Base64-encoded string `s`. This function takes a Base64-encoded string as input and returns the original string that was encoded.
