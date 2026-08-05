---
title: "Changelog"
description: "Release history of Tim Engine."
keywords: ["changelog", "tim engine", "releases", "version history"]
---

# Changelog

All notable changes to Tim Engine are documented here. The changelog is managed with [changer](https://github.com/iffy/changer) in the [tim repository](https://github.com/tim-engine/tim/blob/main/CHANGELOG.md).

## v0.2.6 — 2026-07-27

### New features
- **`input:TYPE` shorthand** — `input:time`, `input:color`, `input:range`, etc. are parsed as `<input type="TYPE">` at the lexer/parser level. Distinguished from Tim's `:` text-content syntax by checking `wsno == 0` (no whitespace before the colon). Only triggers on `input` tags; subsequent attributes (`.class`, `#id`) still apply.
- **`svg` elements** now auto-inject `xmlns="http://www.w3.org/2000/svg"` at parse time, unless you explicitly provide `xmlns`.
- **`@LitElement, ClassName`** — define Lit-style custom HTML elements in Tim. The tag name is derived from the class name (kebab-case). The body supports `@javascript` blocks (concatenated into the class body) and a single `@client` block (the render template compiled to JS template literals). Generates a JavaScript class extending `LitElement` with `connectedCallback`, `render()`, and `customElements.define()`. Client-side only; server-side rendering emits the class as a `<script>` block.

### Fixes
- PHP Linux build — replaced `--passC: staticExec(...)` with `switch("passC", ...)` in `tim.nims`; uses `php-config --include-dir` as primary header discovery on Linux (with pkg-config fallback).
- Clue hardcoded macOS pragmas — wrapped `{.passC:}` / `{.passL:}` in `php_api.nim`, `python_api.nim`, `lua_api.nim` inside `when defined(macosx):` to prevent MacPorts paths from leaking into Linux builds.
- Docs workflow — added `permissions: contents: write` for the `gh-pages` push.
- Ruby extension CI — `tim-ruby/.github/workflows/build.yml` builds the native extension via `repository_dispatch` for x86_64-darwin, arm64-darwin, and x86_64-linux.

## 2026-07-04

### New features
- **Element multiplication** — `tag*N` repeats an HTML element N times with an injected `$i` index variable (0-based). Example: `li*3: $items[$i]` produces three `<li>` elements.
- **`@import "std/..."` system** — populated the stdlibs table and fixed `libobjects.nim` syntax errors; switched `build.nim` to `initCompiler` for stdlib pass-through.
- **Request API** — exposed the Supranim request API as foreign functions callable via `$this.getPath()`, `$this.getMethod()`, `$this.getQuery("key")`, `$this.getHeader("key")`, `$this.getBody()`, `$this.getIp()`, `$this.getUrl()`, `$this.getAgent()`, `$this.getParam("key")`.
- **`@static` compile-time evaluator** — for `for` loops and `if`/`elif`/`else` conditionals. The body is captured as raw text, `{$varName}` / `$varName` patterns are substituted with literal iteration values, then re-parsed by an inner parser. Supports literal arrays and `start..end` integer ranges (e.g. `@static for $x in 1..12:`).
- **Lexer gains `tkIs` / `tkIsNot`** — recognized as infix operators (precedence 5, equal to `==`), with stdlib implementations that compare values at runtime by `TypeId`. *(Note: in the current engine the identity helpers are available as the `is(a, b)` / `isnot(a, b)` functions.)*

### Changes
- Updated stdlib for VanCode v0.1.9 `ValueStorage` API — `Object.fields` changed from `seq[Value]` to `seq[ValueStorage]` (inline primitive storage). All field reads now use `.toValue`, all field writes use `.toStorage`. No functional changes.

### Fixes
- Fixed `addCallable` KeyError in VanCode when the `exportFunctions` key is missing on overloaded function names.
- Exported macros (`macro foo*`) now properly cross module boundaries via `exported = true` in `genMacro`.
- `serve` command no longer hardcodes template paths — reads `compilation.source`, `compilation.output`, and subdirectory paths from `tim.config.yml`.
- Fixed `source` and `output` fields in `tim.config.yml`.
- `parseVarIdent` now handles generic type annotations (`var abc: array[string]`).
- `CompilationPolicy` is now threaded from `engine.config.compilation.policy` into the codegen via `initCompiler`, enabling per-project feature restrictions (imports, stdlib, packages, loops, conditionals, assignments, dynamic libs).
- Ruby gem automation — `release.yml` pushes platform-specific binaries (x86_64-darwin, arm64-darwin, x86_64-linux) to `openpeeps/tim-ruby` on tag releases.
- Removed hardcoded MacPorts paths from Clue's `ruby_api.nim` — uses project-level `pkg-config` instead.
