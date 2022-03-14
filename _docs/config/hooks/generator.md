---
title: Hook Generator
nav_text: Generator
categories: hooks
order: 2
---

To help you get started quickly, you can generate starter hook code. Here are some examples:

## Cheatsheet

    lono new hook # project-level hooks
    lono new hook --blueprint demo

## Project

    $ lono new hook
          create  config/hooks.rb

Produces:

config/hooks.rb

```ruby
before("build",
  execute: "echo 'config/hooks.rb: test project hook for build'",
)

after("build",
  execute: "echo 'config/hooks.rb: test project hook for build'"
)
```

## Blueprint

    $ lono new hook --blueprint demo
          create  app/stacks/demo/config/hooks.rb

Produces:

app/stacks/demo/config/hooks.rb

```ruby
before("apply",
  execute: "echo 'app/blueprints/demo/config/hooks.rb: test blueprint hook for build'",
)

after("apply",
  execute: "echo 'app/blueprints/demo/config/hooks.rb: test blueprint hook for build'"
)
```
