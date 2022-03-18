---
title: Params Layering
nav_text: Params
category: layering
order: 2
---

## Example

We'll go through an example with params. Given a blueprint named `demo` and the following params directory structure:

    config/blueprints/demo/params
    ├── base.env
    ├── dev.env
    └── prod.env

* `base.env` is always evaluated.
* `dev.env` or `prod.env` is evaluated based on `LONO_ENV`.

The `base.env` params are always used, and `prod.env` provides overrides. We can use different instance type for dev and prod like so.

config/blueprints/demo/params/base.env

    InstanceType=t3.micro

config/blueprints/demo/params/prod.env

    InstanceType=m5.large

Lono will use the `InstanceType=m5.large` parameter value with `LONO_ENV=prod`.  Lono will use `InstanceType=t3.micro` for all other `LONO_ENV` values.  Example:

    LONO_ENV=dev  lono up demo # InstanceType=t3.micro
    LONO_ENV=prod lono up demo # InstanceType=m5.large

Remember, params affect templates at runtime. Here's the lifecycle flow to see when the runtime phase happens.

<img src="/img/tutorial/lono-flowchart.png" alt="Stack Created" class="doc-photo lono-flowchart">

