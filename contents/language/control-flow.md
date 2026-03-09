---
title: "Control flow"
description: "How to use control flow statements in Tim Engine, including if statements, loops, and more."
keywords: ["control flow", "tim engine", "if statements", "loops", "documentation"] 
---

## If statements
If statements allow you to execute a block of code based on a condition. In Tim Engine, you can use `if`, `elif`, and `else` to create conditional statements. For example:
```
var age: int = 25
if age < 18:
  p: "You are a minor."
elif age >= 18 and age < 65:
  p: "You are an adult."
else:
  p: "You are a senior."
```


## For loops
For loops allow you to iterate over a sequence of values. In Tim Engine, you can use the `for` keyword to create a for loop. 

```
var fruits = ["apple", "banana", "cherry"]
for $fruit in fruits:
  p: "I like " & $fruit
```

### For in range
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

## Break and continue
You can use `break` to exit a loop early, and `continue` to skip the rest of the current iteration and move to the next one. 
Both `break` and `continue` can be used in `for` and `while` loops. For example:
```
for $i in 0..10:
  if $i == 5:
    break  // exit the loop when i is 5
  if $i % 2 == 0:
    continue  // skip even numbers
  p: "The value of i is " & $i
```

