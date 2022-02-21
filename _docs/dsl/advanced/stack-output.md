---
title: Stack Output
category: dsl-advanced
desc: Can be used in params files with ERB to lookup outputs from other stacks.
---

The `output` method can be used in [params]({% link _docs/config/params.md %}) files to reference outputs in other stacks.

Let's say you have deployed a stack named `vpc`.

    lono up vpc

The vpc stack has been designed with a `VpcId` output.

Then you would like to launch another stack that has a `VpcId` parameter. You can use the `output` method to look up the value dynamically. Here's the general form:

    VpcId=<%= output("BLUEPRINT.LOGICAL_ID") %>

Example:

config/blueprints/demo/params/dev.txt:

    VpcId=<%= output("vpc.VpcId") %>

The vpc stack's `VpcId` output us used as the `VpcId` parameter for the demo stack:

    lono up demo # will use the VpcId parameter from `output` of the blueprint stack

The helpers are also documented in [Built-In Helpers]({% link _docs/helpers/builtin.md %}).

You can also use `stack_output` instead of `output`. Within the params context, `output` is aliased to `stack_output`.

config/blueprints/demo/params/dev.txt:

    VpcId=<%= stack_output("vpc.VpcId") %>

## Conventions

Notice that we specify the blueprint name not the stack name. So:

    VpcId=<%= output("vpc.VpcId") %>      # correct
    # vs
    VpcId=<%= output("vpc-dev.VpcId") %>  # incorrect

Lono conventionally appends the stack name with the `LONO_ENV`. This allows us to use the same blueprint name in the `output` helper and keeps the code consistent. However, this behavior can be changed for the entire lono project if needed. You just have to override the default `config.names.stack_output` pattern.

config/app.rb

```ruby
Lono.configure do |config|
  config.names.output.stack = ":BLUEPRINT-:ENV" # default
  config.names.output.expand = true # change to false to disable expansion
end
```

If you're wondering why `LONO_APP` is not in the default. It's usually more common that companies have multiple apps running the same dev or prod VPC. Lono provides some reasonable defaults, but they can be overriden.

Additionally, if you just need to override it for a specific parameter. Just pass in the pattern directly. When a `:` is in the passed value, lono will use it for expansion. Example:

config/blueprints/demo/params/base.txt:

    VpcId=<%= output("vpc-:ENV.VpcId") %> # another way to override the default expansion pattern
    # When LONO_ENV=dev the above is the same as
    VpcId=<%= output("vpc-dev.VpcId") %>

{% include back_to/dsl-basics.md %}
