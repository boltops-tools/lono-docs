---
title: Ruby Hooks
nav_text: Ruby
categories: hooks
order: 3
---

The hook `execute` option can also be provided Ruby code instead of a string.  Here's how it works:

1. When the execute option is a String: Lono will shell out and run it as a script.
2. When the execute option is a Ruby object: Lono will perform the `call` method on the object or class.

## Ruby Class

When the Ruby object is a class with an instance method `call`, Lono creates a new instance of the class and runs its `call` method.  Example:

config/hooks.rb

```ruby
class EnvExporter
  def call
    ENV['SECRET_FOO'] = "bar"
  end
end

before("build",
  execute: EnvExporter,
)
```

Lono will do something like this:

```ruby
EnvExporter.new.call
```

The example sets the `SECRET_FOO` environment variable. It is then available to the DSL in the blueprints.

## Ruby Object

When the Ruby object, Lono expects it to have a `call` method and will run it.  Example:

config/hooks.rb

```ruby
before("compile",
  execute: lambda { ENV['SECRET_FOO'] = "hi2" }
)
```

Lono will do something like this:

```ruby
@hook[:execute].call
```

## Method Argument

The `call` method can optionally be defined with an argument. The argument can be named whatever you wish. It's named `runner` in the example. The `runner` argument is the instance of the class that handles running the hook.  It can be use to access metadata about the running lono command. An example may help:

app/blueprints/demo/config/hooks.rb

```ruby
class ShowContext
  def call(runner)
    blueprint = runner.blueprint

    puts "runner #{runner}"
    puts "runner.hook #{runner.hook}"

    puts "blueprint #{blueprint}"
    puts "blueprint.name #{blueprint.name}"
    puts "blueprint.build_dir #{blueprint.build_dir}"
    puts "blueprint.cache_dir #{blueprint.cache_dir}"
    puts "blueprint.root #{blueprint.root}"
    puts "blueprint.type #{blueprint.type}"
    puts "blueprint.type_dir #{blueprint.type_dir}"
    puts "blueprint.options #{blueprint.options}"

    puts("Lono.root #{Lono.root}")
    puts("Lono.env #{Lono.env}")
  end
end

before("build",
  execute: ShowContext,
)
```

The example puts out some example values accessible via the `runner` object.