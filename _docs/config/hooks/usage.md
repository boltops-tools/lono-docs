---
title: Lifecycle Hooks Usage
nav_text: Usage
categories: hooks
order: 1
---

You can use hooks to run scripts at specific steps of the Lono lifecycle.

## Lifecycle Hooks

Hook | Description
---|---
build | When Lono builds or compiles the Lono project to the `.lono-cache` folder.
down | When Lono destroys the stack.
up | When Lono creates or updates the stack.

{% include config/hooks/generator.md %}

## Example

config/hooks.rb

```ruby
before("build",
  execute: "echo hi",
)

after("build",
  execute: "echo bye"
)
```

## exit on fail

By default, if the hook commands fail, then lono will exit with the original hook error code.  You can change this behavior with the `exit_on_fail` option.

```ruby
before("build",
  execute: "/command/will/fail/but/will/continue",
  exit_on_fail: false,
)
```

In this case, regardless of the hook command succeeding or failing, Lono will continue right along.

{% include config/hooks/options.md command="lono" %}

## Boot Hooks

If you need to hook into the Lono boot process super-early on, check out [Boot Hook]({% link _docs/config/boot.md %}).

{% include config/hooks/context.md %}
