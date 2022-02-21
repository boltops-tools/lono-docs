---
title: Initializers
nav_text: Initializers
category: config
order: 8
---

Config initializers allow you to hook early into the Lono boot process.  This provides a way of customizing Lono beyond the [config/app.rb]({% link _docs/config/reference.md %}) options. Generally, recommend using config options when possible and reaching for config initializers for advanced usage.

Here's a simple example:

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

This example customizes Lono layering processing. More info: [Custom Layering]({% link _docs/layering/custom.md %}).

Config initializers are a generalized system, so the way you use it really depends on what you're trying to do.
