---
title: "HTTP Server & Configuration"
description: "Use Tim Engine as a built-in HTTP server with routing, live reload, and the tim.config.yml configuration file."
keywords: ["server", "http", "serve", "live reload", "websocket", "tim.config.yml", "configuration", "browser sync"]
---

Tim Engine ships with a built-in HTTP server powered by [Supranim](https://github.com/supranim/supranim). You can use it to compile and serve your templates at runtime with routing, middleware, WebSocket connections and automatic live reload during development.

## Starting the server

Create a `tim.config.yml` in your project, then run:

```
tim serve tim.config.yml
```

The server will precompile all your templates, start a file watcher on your `layouts`, `views` and `partials` directories, and start serving on the configured port (default `8000`).

Static files are served from the `public/` directory next to your config file.

## tim.config.yml

A typical project configuration looks like this:

```yaml
type: project
description: "A simple Tim Engine front-end application"
version: "0.1.0"
license: "MIT"

compilation:
  source: "./templates"
  output: "./build"
  release: false
  policy:
    disallow:
      - loops
      - loadDynlib

server:
  port: 8000
  threads: 1
  routes:
    "/": "index"
    "/error": "error"

browser_sync:
  port: 3500
  delay: 200
```

### `compilation`
| Field | Description |
|---|---|
| `source` | The directory containing your templates. Subdirectories `layouts/`, `views/` and `partials/` are derived from it. |
| `output` | The directory where compiled output (AST, opcache, HTML) is written. |
| `release` | Set to `true` in production. |
| `policy` | Per-project feature restrictions — see [Compilation Policy](#compilation-policy). |

### `server`
| Field | Description |
|---|---|
| `port` | The port the HTTP server listens on (default `8000`). |
| `threads` | Number of worker threads. A value greater than `1` enables multi-threading. |
| `routes` | A map of URL paths to view names, e.g. `"/": "index"` renders the `index` view. |

### `browser_sync`
| Field | Description |
|---|---|
| `port` | The WebSocket port used for live reload notifications. |
| `delay` | Delay (in milliseconds) before reloading after a file change. |

## Live reload

The `serve` command starts a WebSocket server and watches your template files. Whenever a layout, view or partial changes, the affected templates are recompiled and connected browsers are notified to reload automatically.

## Request API

Inside your templates you can access the current HTTP request through `$this` using the following functions:

| Function | Description |
|---|---|
| `$this.getPath()` | The request path, e.g. `/blog/post-1` |
| `$this.getMethod()` | The HTTP method, e.g. `GET` |
| `$this.getQuery("key")` | A query string parameter |
| `$this.getHeader("key")` | A request header |
| `$this.getBody()` | The raw request body |
| `$this.getIp()` | The client IP address |
| `$this.getUrl()` | The request URL |
| `$this.getAgent()` | The `User-Agent` header |
| `$this.getParam("key")` | A route parameter |
| `$this.isDevel()` | `true` when running in development mode |
| `$this.getConfig()` | The resolved engine configuration as JSON |

Example:
```
p: "You requested $this.getPath()"
```

## Compilation Policy

The `compilation.policy.disallow` list lets you restrict which features a project is allowed to use. Each disallowed feature raises an error at compile time:

| Policy kind | Description |
|---|---|
| `stdlib` | Standard library usage |
| `packages` | Package imports |
| `imports` | Import statements |
| `loops` | `for` and `while` loops |
| `conditionals` | `if` / `elif` / `else` |
| `assignments` | Variable assignments |
| `loadDynlib` | Loading dynamic libraries via FFI |

```yaml
compilation:
  policy:
    disallow:
      - loops
      - conditionals
```

## CLI flags

The `src` command (the default command, so `tim file.timl` works) supports the following flags:

| Flag | Description |
|---|---|
| `--ext:<target>` | Target output: `html` (default), `js`, `py`, `rb`, `php`, `lua`, `nim` |
| `-o <file>` | Write the output to a file instead of stdout |
| `--data <json>` | JSON data passed to the template — keys `app` (global, `$app`) and `this` (local, `$this`) |
| `--bench` | Print the elapsed time |
| `--nocache` | Rebuild the cache instead of using cached modules |
| `--sync` | Enable sync and reload for development *(work in progress)* |

The `ast` command serializes a template into an AST representation written next to the source file:

```
tim ast example.timl
```
