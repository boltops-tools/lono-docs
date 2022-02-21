---
title: Lono Concepts
nav_text: Concepts
categories: intro
order: 2
---

Here are main Lono concepts:

* [Blueprints]({% link _docs/blueprints.md %})
* [Params]({% link _docs/config/params.md %})
* [Variables]({% link _docs/config/variables.md %})
* [Layering]({% link _docs/layering.md %})
* [Helpers]({% link _docs/helpers.md %})

## Blueprints

Lono blueprints encapsulate the code used to build CloudFormation templates and infrastructure resources. Blueprints are what you'll mostly work with and can live in `app/blueprints`  The simplest blueprint struture is:

    app/blueprints/demo
    └── template.rb

Docs: [Blueprints]({% link _docs/blueprints.md %})

## Params

CloudFormation parameters allow you to create different environments with the same template code. Lono params simplify this process by providing an env-like file syntax. Here's an example:

config/blueprints/demo/params/dev.txt:

    KeyName=default
    InstanceType=t2.micro

Docs: [Params]({% link _docs/config/params.md %})

## Variables

Lono Variables allow you to compile down different templates when run-time [params]({% link _docs/config/params.md %}) do not suffice. This allows doing things that are outside of the ability of CloudFormation run-time parameters. Here's an example:

config/blueprints/demo/vars/dev.txt:

```ruby
@desc = "Template description"
```

Docs: [Variables]({% link _docs/config/variables.md %})

## Layering

Lono supports a concept called Layering.  Layering allows you to build both prod and dev environments with the same template code. Here's an simple example of layering:

    config/blueprints/demo/params
    ├── dev.txt
    └── prod.txt

Docs: [Layering]({% link _docs/layering.md %})

## Helpers

Helpers methods allow you to extend the Lono DSL. With [Custom Helpers]({% link _docs/helpers/custom.md %}) you can define your own helper methods. Lono also comes with some [built-in helper methods]({% link _docs/helpers/builtin.md %}).

Docs: [Helpers]({% link _docs/helpers.md %})
