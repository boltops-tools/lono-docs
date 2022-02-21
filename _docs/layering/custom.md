---
title: Custom Layering
nav_text: Custom Layering
category: layering
order: 5
---

If Lono built-in layering does not work for your needs, you can customize the way Layering is done.

Custom layering is an advanced use-case. It is generally recommended to stick to the Lono conventions, which is already quite powerful and others won't have to learn the customization.

## Structure

To fully customize layering, you redefine the `Lono::Layering` module. Here's a starter structure:

config/inits/layering.rb

```ruby
Lono::Layering.module_eval do
  # def pre_layers
  #   []
  # end
  #
  # def main_layers
  #   super
  # end
  #
  # def post_layers
  #   []
  # end
end
```

Note: Make sure to use `module_eval` or require `lono/layering` first. This ensures that the existing Lono Layering definition is first loaded and then you can add your own customizations. You can also use the `ActiveSupport.on_load(:lono_layering)` hook instead if you prefer not use `module_eval`. Example:

config/inits/layering.rb

```ruby
ActiveSupport.on_load(:lono_layering) do
  module Lono::Layering
    # ...
  end
end
```
## Interface Methods

There are 3 main interface methods designed to be overriden:

1. **pre_layers**: Layers that get processed before the main layer. Defaults to an empty Array.
2. **main_layers**: The main layers that get processed as described by the Lono docs. This includes the base and env layers as well as the layers provided by the specific cloud plugins. IE: AWS, Azure, GCP.
3. **post_layers**: Layers that get processed after the main layer. Defaults to an empty Array.

You can chose the methods to override.

## Example

Let's override the `pre_layers` method as an example:

config/inits/layering.rb

```ruby
Lono::Layering.module_eval do
  def pre_layers
    [
      "teams/#{ENV['TEAM']}",
    ]
  end
end
```

The `pre_layer` adds a layer using the `TEAM` env var. For example:

config/blueprints/demo/params/teams/backend.txt

    team_scoped_config="team_scoped_config_value"

    $ TEAM=backend lono build demo

Also see [Debugging Layering]({% link _docs/layering/debugging.md %}).
