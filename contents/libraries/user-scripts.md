---
title: "User Scripts"
description: "Inject custom scripts into the Tim scripting environment"
keywords: ["custom library", "ffi", "foreign function interface", "library creation"]
---

The User Scripts feature allows you to inject custom Nim code into the Tim scripting environment, enabling you

## User scripts
This feature is available only in Nim, and allows you to define custom functions that can be called from within your application's scripting environment. This is particularly useful for creating reusable code snippets, utility functions, or even integrating third-party libraries into your application. For example:

```nim
import tim
import pkg/vancode/interpreter/[value, sym]

# initialize Tim engine like you normally would
var timEngine*: TimEngine = newTim(
  src = "templates", output = "build", basepath = getCurrentDir()
)

# Now, you can add custom functions to the scripting environment
timEngine.userScript.addProc(
  "hello",
  @[paramDef("name", ttyString)],
  ttyString,
  proc (args: StackView, argc: int): Value =
    return initValue("Hello, " & args[0].stringVal[] & "!")
)
```

Calling this from a `.timl` script would look like this:

```
echo hello("Tim") // Output: Hello, Tim!
```
