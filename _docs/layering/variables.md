---
title: Variables Layering
nav_text: Variables
category: layering
order: 3
---

## Example

Given a blueprint named `demo` and the following vars directory structure:

    config/blueprints/demo/vars
    ├── base.rb
    ├── dev.rb
    └── prod.rb

* `base.rb` is always evaluated.
* `dev.rb` or `prod.rb` is evaluated based on LONO_ENV.

The `base.rb` params are always used, and `prod.rb` provides overrides. We can use different autoscaling group min and max size for dev and prod like so.

config/blueprints/demo/vars/base.rb

```ruby
@min_size = 1
@max_size = 1
```

config/blueprints/demo/vars/prod.rb

```ruby
@min_size = 10
@max_size = 20
```

Lono will use the `@max_size = 20` variable value with `LONO_ENV=prod`.  Lono will use `@max_size = 1` for all other `LONO_ENV` values.  Example:

    LONO_ENV=dev  lono up demo # @max_size = 1
    LONO_ENV=prod lono up demo # @max_size = 20

Remember, variables affect templates at compile-time. Here's the lifecycle flow to see when the compile phase happens.

<img src="/img/tutorial/lono-flowchart.png" alt="Stack Created" class="doc-photo lono-flowchart">
