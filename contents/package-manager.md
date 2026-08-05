---
title: "Manage Packages"
description: "Install, create, and publish packages in Tim Engine to extend its functionality and share your code with the community."
keywords: ["package manager", "tim engine", "install packages", "create packages", "publish packages", "documentation"]
---

Tim engine has a built-in package manager that allows you to easily install, create, and publish packages. A package is a collection of reusable code, such as functions, macros, or components, that can be shared and reused across different projects.

Manage packages in Tim Engine:

- [Creating a Package](/package-manager/create-package): Learn how to create a package to organize and share your reusable code.
- [Publishing a Package](/package-manager/publish-package): Share your package with the world by publishing it to the Tim Engine package registry.

### Package location
Tim Engine looks for packages in the `~/.tim/packages` directory. This directory is automatically created when you use Tim Engine for the first time. When you install a package using the package manager, it will be downloaded and stored in this directory.

### Package manager commands
The CLI ships with the following package commands:

- `tim init` — initialize a new package or project structure
- `tim remove <pkg>` — remove an installed package
- `tim develop <pkg>` — create a symlink to a package in local source *(work in progress)*
- `tim install <github-url>` — install a package from a remote source *(work in progress)*
- `tim publish` — publish a package to the registry *(not yet available)*

### Developing packages
When developing a package, you can create a symbolic link from your package directory to the `~/.tim/packages` directory. This allows you to test your package locally without having to publish it. For example:
```
ln -s /path/to/your/package ~/.tim/packages/your-package
```
