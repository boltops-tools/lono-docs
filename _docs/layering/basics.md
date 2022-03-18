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

Params have a `.env` extension, and vars have a `.rb` extension. We'll show a params example to cover the basics of layering.

    config/blueprints/demo/params
    ├── base.env
    ├── dev.env
    └── prod.env

* `base.env` is always evaluated.
* `dev.env` or `prod.env` is evaluated based on `LONO_ENV`.

In this case, you want to define your base params used for templates in the `base.env` and overrides in `prod.env`.

The basic example above shows layering with the top-level `config` folder.  You can also define layers within the blueprint.

{% include layering/separate-layers.md %}

## More

More step-by-step docs are provided in the next documentation pages and go into more details on layering.

* [Params]({% link _docs/layering/params.md %})
* [Variables]({% link _docs/layering/variables.md %})
* [Full Layering]({% link _docs/layering/full.md %})
