---
title: Blueprint Generator
nav_text: Blueprint
category: generators
order: 1
---

You can use `lono new module` to create the a starter module structure. Example:

    $ lono new blueprint demo
    => Creating new blueprint called demo.
          create  app/blueprints/demo
          create  app/blueprints/demo/template.rb
    $

The starter blueprint is blank.

app/blueprints/demo/template.rb

```ruby
# This is where you put your infrastructure code
# Docs: https://lono.cloud/docs/dsl/
```

If you would like the blueprint to include some example code, use the `--examples` option.

    lono new blueprint demo --examples
