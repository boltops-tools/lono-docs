---
title: Variables
nav_text: Variables
category: config
order: 4
---

Lono Variables allow you to compile down different templates when run-time [params]({% link _docs/config/params.md %}) do not suffice. This allows doing things that are outside of the ability of CloudFormation run-time parameters. Effective use of variables can dramatically reduce the amount of code you have to write.

## Use Responsibly

Generally, it is recommended to use parameters when possible and drop down to variables when needed. This keeps you closer to CloudFormation's native abilities. However, sometimes varables can dramatically clean up your code and make it more readable. It depends.

## Structure

The variables are defined in the `config/blueprints/BLUEPRINT/vars` folder.

    config/blueprints/demo/vars
    ├── dev.rb
    └── prod.rb

## Examples

The variables files are simply Ruby code where you set instance variables (variables with an @ sign in front). The instance variables are made available to templates, helpers, and params within the blueprint.

Here's an example:

config/vars/base.rb:

```ruby
@ami = "ami-base"
```

The `@ami` variable is now available to all of your templates.

Here's an another example:

config/vars/prod.rb:

```ruby
@ami = "ami-prod"
```

The `@ami = "ami-prod"` variable will be used when `LONO_ENV=prod`.

<img src="/img/tutorial/lono-flowchart.png" alt="Stack Created" class="doc-photo lono-flowchart">

## Layering Support

Variables also support layering. Layering support is covered in [Layering Support]({% link _docs/layering.md %}).
