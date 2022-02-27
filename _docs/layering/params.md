---
title: Params Layering
nav_text: Params
category: layering
order: 2
---

## Params Example

We'll go through an example with params. Given a blueprint named `demo` and the following params directory structure:

    config/blueprints/demo/params
    ├── base.txt
    ├── dev.txt
    └── prod.txt

* `base.txt` is always evaluated.
* `dev.txt` or `prod.txt` is evaluated based on `LONO_ENV`.

In this case, you want to define your base params used for templates in the `base.txt` and overrides in `prod.txt`. For example, let's say we want a different instance type for dev and prod. We could have something like this:

config/blueprints/demo/params/base.txt:

    InstanceType=t3.micro

config/blueprints/demo/params/prod.txt:

    InstanceType=m5.large

Lono will use the `InstanceType=m5.large` parameter value when launching the stack with `LONO_ENV=prod`.  Lono will use `InstanceType=t3.micro` for all other `LONO_ENV` values.  Example:

    LONO_ENV=dev  lono up demo # InstanceType=t3.micro
    LONO_ENV=prod lono up demo # InstanceType=m5.large

Remember params can be used to affect templates at run-time. Here's the lifecycle flow to see when the run-time phase happens.

<img src="/img/tutorial/lono-flowchart.png" alt="Stack Created" class="doc-photo lono-flowchart">

