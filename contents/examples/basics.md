---
title: "Basic examples"
description: "Here are some basic examples of using Tim Engine to create HTML templates and scripts."
keywords: ["Tim Engine", "examples", "basics", "HTML templates", "scripting"]
---

We are going to cover some basic examples of using Tim Engine to create HTML templates and scripts. These examples will demonstrate the core features of Tim Engine and how to use them effectively. We are going to use Bootstrap for styling in our examples, but you can use any CSS framework or custom styles you prefer.


## Basic HTML Template
Here's a simple example of a Tim Engine template that generates a basic HTML page:
```
html
  title: "Hello, Tim Engine!"
  meta charset="utf-8"
  meta name="viewport" content="width=device-width, initial-scale=1"
  link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/css/bootstrap.min.css" rel="stylesheet"
  body
    div.container > div.row > div.col-md-12.text-center
      h1: "Hello, Tim Engine!"
      p: "This is a basic example of a Tim Engine template using Bootstrap for styling."

    // include Bootstrap JavaScript bundle for interactive components
    script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/js/bootstrap.bundle.min.js"
```

## Create a form
```text
div.mb-3
  label.form-label for="exampleFormControlInput1": "Email address"
  input.form-control type="email" id="exampleFormControlInput1" placeholder="name@example.com"

div.mb-3
  label.form-label for="exampleFormControlTextarea1": "Example textarea"
  textarea.form-control id="exampleFormControlTextarea1" rows="3": "This is a textarea example."
```


### Create a modal
```text
div.modal tabindex="-1" > div.modal-dialog > div.modal-content
  div.modal-header
    h5.modal-title: "Modal title"
    button.btn-close type="button" data-bs-dismiss="modal" aria-label="Close"
  div.modal-body
    p: "This is the content of the modal."
  div.modal-footer
    button.btn.btn-secondary type="button" data-bs-dismiss="modal": "Close"
    button.btn.btn-primary type="button": "Save changes"
```

### Embed JavaScript
Tim allows you to embed JavaScript directly within your templates using the `@javascript` block. Here's an example of how to add a click event listener to a button:
```text
a.btn.btn-primary: "Learn More"

@javascript
  document.addEventListener("DOMContentLoaded", () => {
    document.querySelector('.btn').addEventListener('click', () => {
      console.log("Hello, World!")
    });
  })
@end
```