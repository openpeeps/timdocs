---
title: "Transpilation Overview"
description: "An overview of the source to source transpilation process in Tim Engine and the benefits it provides for developers using the engine."
keywords: ["transpilation", "overview", "tim engine is Awesome!", "template engine", "scripting language"]
---

## What's up with transpilation?
Transpilation is the process of converting source code from one programming language to another. In this case, Tim is capable of transpiling its own scripting language into multiple target languages, such as **JavaScript**, **Python**, **PHP**, **Lua**, **Ruby** and **Nim**. This allows developers to write their templates in Tim's scripting language while still being able to use the generated code in their preferred programming language.

<div class="alert alert-info rounded-4" role="alert">
  <div class="alert-content">
    The S2S transpilation process in Tim Engine is still in its early stages of development. The design and implementation of the transpiled code is subject to change as we continue to refine the process and gather feedback from developers.
  </div>
</div>

> [!NOTE]
> The generated class, proc or function name is derived from the input file name (converted to CamelCase). Transpiling `example.timl` produces a `Example` class, `Test.timl` produces `Test`, and so on. The examples below use `Test.timl` as the input.

## Benefits of transpilation
Transpilation allows developers to write their templates in Tim's scripting language while still being able to use their favorite stack, tools and programming languages.

The front-end migration process can be a daunting task. Having your front-end logic written in scripting language like Tim can make the transition smoother, as you can transpile your existing code to the target language without having to rewrite it from scratch.

<div class="alert alert-info rounded-4" role="alert">
  <div class="alert-content">
    A pluggable transpilation engine is also in the works, which will allow developers to create custom transpilation targets and extend the capabilities of the transpilation process.
  </div>
</div>

### JavaScript
Transpiling a Tim template to JavaScript is straightforward. Here, we have a simple Tim template that includes a variable and some HTML elements:
```
div.container
  var name = "Tim Engine is Awesome!"
  p: $name
```

Now, using the `src` command, we can pass `--ext:js` to specify the target language for transpilation:
```text
tim src example.timl --ext:js
```

The resulting JavaScript code would look something like this:
```js
class Test {
  static render(locals = {}, app = {}) {
    let html = "";
    html += `<div class=\"container\">`;
    /** @type {string} */
    let name = "Tim Engine is Awesome!";
    html += `<p>`;
    html += String(name);
    html += `</p>`;
    html += `</div>`;
    return html;
  }
}
module.exports = Test;
```

As you can see from the example, the Tim template is transpiled into a JavaScript class with a static `render` method that generates the HTML output. The variable `name` is defined and used within the method, demonstrating how the scripting language is transpiled into JavaScript code.

### Nim language
Transpiling the same template into Nim is possible with the `--ext:nim` flag:
```text
tim src example.timl --ext:nim
```

The resulting Nim code would look like this:
```nim
import std/[json]

proc getTestView*(locals, app: JsonNode = newJObject()): string =
  var result = ""
  add result, "<div class=\"container\">"
  var name = "Tim Engine is Awesome!"
  add result, "<p>"
  add result, $name
  add result, "</p>"
  add result, "</div>"
  move(result)
```

### Ruby
Transpiling the same template into Ruby is also possible using the `--ext:rb` flag. This will generate the following Ruby code:
```ruby
class Test
  # @param locals [Hash] Local data
  # @param app [Hash] Global data
  # @return [String] The generated HTML.
  def self.render(locals = {}, app = {})
    html = +""
    html << "<div class=\"container\">"
    name = "Tim Engine is Awesome!"
    html << "<p>"
    html << "#{ name }"
    html << "</p>"
    html << "</div>"
    html
  end
end
```

### Python
Switching from Ruby to Python is as simple as changing the `--ext` flag to `--ext:py`. The resulting Python code would look like this:
```python
class Test:
    @staticmethod
    def render(locals=None, app=None):
        html = []
        html.append(f'<div class=\"container\">')
        # type: name: Any
        name = 'Tim Engine is Awesome!'
        html.append(f'<p>')
        html.append(str(name))
        html.append('</p>')
        html.append('</div>')
        return ''.join(html)
```

### Lua
Transpiling to Lua is also supported. By using the `--ext:lua` flag, the generated Lua code would look like this:
```lua
local Test = {}

-- @param args Table
-- @return string The generated HTML.
function Test.render(args)
  local app = args.app or {}
  local this = args.this or {}
  local html = ''
  html = html .. "<div class=\"container\">"
  local name = "Tim Engine is Awesome!"
  html = html .. "<p>"
  html = html .. tostring(name)
  html = html .. "</p>"
  html = html .. "</div>"
  return html
end
return Test
```

### PHP
Transpiling to PHP is also supported. By using the `--ext:php` flag, the generated PHP code would look like this:
```php
<?php
class Test {
  static function render($locals = [], $app = []) {
    $html = '';
    $html .= "<div class=\"container\">";
    // @var $name: string
    $name = "Tim Engine is Awesome!";
    $html .= "<p>";
    $html .= $name;
    $html .= "</p>";
    $html .= "</div>";
    return $html;
  }
}
```
