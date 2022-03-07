---
title: Restricting Envs
nav_text: Envs
categories: restricting
---

If you want to restrict environments that can be deployed, you can use the following. Restricting environments that can be deployed can prevent typo mistakes and accidentally creating resources for different LONO_ENVs.

config/app.rb

```ruby
Lono.configure do |config|
  config.allow.envs = ["dev", "prod"]
  # config.deny.envs = ["qa"]
end
```

{% include config/restricting/deny-wins.md %}

## Example 1: Simple Allow

Let's say we have a demo blueprint:

    $ lono list
    app/blueprints/demo

config/app.rb

```ruby
Lono.configure do |config|
  config.allow.envs = ["dev", "prod"]
end
```

Since only the dev and prod env is allowed, you would not be able to deploy to any other LONO_ENV. Example:

    $ LONO_ENV=qa lono up demo
    ERROR: The configs do not allow this.
    This env is not allowed to be used: LONO_ENV=qa
    Allowed envs: dev, prod
    $

## Example 2: Simple Deny

Let's say we have a stack:

    $ lono list
    app/blueprints/demo

config/app.rb

```ruby
Lono.configure do |config|
  config.deny.envs = ["qa"]
end
```

You can deploy to any environment except `LONO_ENV=qa`. Example:

    $ LONO_ENV=qa lono up stack1
    ERROR: The configs do not allow this.
    This env is not allowed to be used: LONO_ENV=qa
    Deny envs: qa
    $

## Example 3: Complete Customization

For even more control over which environments are allowed, you can assign an object that implements `call` and returns an Array. This is an advanced technique. Example:

config/app.rb

```ruby
class AllowEnvs
  def call(blueprint)
    if blueprint.name == "route53"
      ["global"]
    else
      ["dev", "prod"]
    end
  end
end
class DenyEnvs
  def call(blueprint)
    # returns nil when nothing provided
  end
end

Lono.configure do |config|
  config.allow.envs = AllowEnvs
  config.deny.envs = DenyEnvs
end
```

The `AllowEnvs` class defines the `call` method and takes the `stack` argument. Its value is the name of the current stack being deployed. The `AllowEnvs` and `DenyEnvs` classes should return an Array or nil. Returning `nil` is the same as not setting the option.
