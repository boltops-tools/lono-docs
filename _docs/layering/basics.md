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

## Top-Level Folders: app vs config

The basics example above shows layering with the top-level `config` folder.  You can also define your params and vars in the top-level `app` folder. Here's an example of the different paths:

    app/blueprints/demo/config/params - processed first
    config/blueprints/demo/params - processed later and takes higher precedence

Generally, it's recommended to set your custom params and vars in the top-level `config` folder. The blueprint will define defaults in the `app/blueprints/demo` folder.

## More

More step-by-step docs are provided in the next documentation pages and go into more details on layering.

* [Params]({% link _docs/layering/params.md %})
* [Variables]({% link _docs/layering/variables.md %})
* [Full Layering]({% link _docs/layering/full.md %})
