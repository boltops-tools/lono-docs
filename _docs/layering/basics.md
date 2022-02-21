---
title: Layering Basics
nav_text: Basics
category: layering
order: 1
---

## Basics

Layering generally works the same for params and variables files. They use different folders. Example:

    config/blueprints/demo/params
    config/blueprints/demo/vars

Params have a `.txt` extension and vars have a `.rb` extension. We'll show a params example to cover the basics of layering.

    config/blueprints/demo/params
    ├── base.txt
    ├── dev.txt
    └── prod.txt

* `base.txt` is always evaluated.
* `dev.txt` or `prod.txt` is evaluated based on `LONO_ENV`.

In this case, you want to define your base params used for templates in the `base.txt` and overrides in `prod.txt`.

More step-by-step docs are provided below:

* [Params]({% link _docs/layering/params.md %})
* [Variables]({% link _docs/layering/variables.md %})
