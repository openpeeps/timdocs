---
title: "Installation"
description: "🚀 Get Tim Engine up and running in no time! Follow our simple installation"
---


## Building from Source
To install Tim Engine, you can use `nimble` to build from source. Read the [Nim installation guide](https://nim-lang.org/install.html) if you don't have Nim installed.

Once you have Nim installed, you can run the following command to install Tim Engine:
```
nimble install tim
```

Once installed, nimble will place the `tim` binary in its bin directory, which is typically `~/.nimble/bin` on Unix-like systems. Make sure to add this directory to your system's PATH environment variable to access the `tim` command from anywhere in your terminal.

## Download pre-built binaries
You can download pre-built binaries for your platform from the [releases page](https://github.com/openpeeps/tim/releases). Simply download the appropriate binary for your operating system, extract it, and add it to your system's PATH.

## Use Tim for Node.js
If you prefer to use Tim Engine from your Node/Bun projects, you can install the `@openpeeps/tim` native add-on package from npm:
```
npm install @openpeeps/tim
```

