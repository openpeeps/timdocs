---
title: "Control flow"
description: "How to use control flow statements in Tim Engine, including if statements, loops, and more."
keywords: ["control flow", "tim engine", "if statements", "loops", "documentation"] 
---

## If statements
If statements allow you to execute a block of code based on a condition. In Tim Engine, you can use `if`, `elif`, and `else` to create conditional statements. For example:
```
var fruits = ["apple", "banana", "cherry", "apricot", "avocado"]
if $fruits[0] == "apple":
  p: "This is an apple."
elif $fruits[1] == "banana":
  p: "This is a banana."
else:
  p: "This is a fruit."
```

## For loops
For loops allow you to iterate over a sequence of values. In Tim Engine, you can use the `for` keyword to create a for loop. 

```
var fruits = ["apple", "banana", "cherry"]
for $fruit in $fruits:
  p: "I like " & $fruit
```

## For in range
Here is an example using the `..` operator to create a range of numbers:
```
for $i in 0..5:
  p: "The value of i is " & $i
```

## While loops
While loops allow you to execute a block of code as long as a condition is true. In Tim Engine, you can use the `while` keyword to create a while loop. For example:
```
var count: int = 0
while $count < 5:
  p: "Count is " & $count
  inc($count)
```

## Break
You can use `break` to exit a loop early. For example:
```
var count: int = 0
while $count < 10 {
  if $count == 5:
    break  // exit the loop when count is 5
  p: "The value of count is " & $count
  inc($count)
}
```

> [!NOTE]
> `break` is fully supported in `while` loops. `break` and `continue` inside `for` loops are not yet implemented — avoid them for now. `continue` is recognized by the lexer but not implemented in the engine.

