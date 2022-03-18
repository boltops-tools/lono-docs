---
title: Layering Debugging Tips
nav_text: Debugging
category: layering
order: 88
---

Lono layering is a powerful ability. While some folks love layering, some dislike it. Think this is because layers are so powerful that they can get complex, especially when abused. It's up to the welder of the sword. This doc tries to help you debug layering, even when abused. 🤣

## Seeing Layers Clearly

Probably the best tip is to configure `config.layering.show` so you can see the layers.

config/app.rb

```ruby
Lono.configure do |config|
  config.layering.show = true
end
```

This will show the **found** layers. Example:

    $ lono build demo
    Params Layers:
        config/blueprints/demo/params/base.env
        config/blueprints/demo/params/dev.env

## All Layering

To see all the **possible** layers is to set `LONO_LAYERS_ALL=1`.

    export LONO_LAYERS_ALL=1

There are many layers, so we'll only show the params one.

    app/blueprints/demo/config/params.env
    app/blueprints/demo/config/params/base.env
    app/blueprints/demo/config/params/dev.env
    app/blueprints/demo/config/params/us-west-2.env
    app/blueprints/demo/config/params/base/us-west-2.env
    app/blueprints/demo/config/params/dev/us-west-2.env
    app/blueprints/demo/config/params/111111111111.env
    app/blueprints/demo/config/params/base/111111111111.env
    app/blueprints/demo/config/params/dev/111111111111.env
    app/blueprints/demo/config/params/111111111111/us-west-2.env
    app/blueprints/demo/config/params/base/111111111111/us-west-2.env
    app/blueprints/demo/config/params/dev/111111111111/us-west-2.env
    config/blueprints/demo/params.env
    config/blueprints/demo/params/base.env
    config/blueprints/demo/params/dev.env
    config/blueprints/demo/params/us-west-2.env
    config/blueprints/demo/params/base/us-west-2.env
    config/blueprints/demo/params/dev/us-west-2.env
    config/blueprints/demo/params/111111111111.env
    config/blueprints/demo/params/base/111111111111.env
    config/blueprints/demo/params/dev/111111111111.env
    config/blueprints/demo/params/111111111111/us-west-2.env
    config/blueprints/demo/params/base/111111111111/us-west-2.env
    config/blueprints/demo/params/dev/111111111111/us-west-2.env

As you can see, layering can be pretty powerful but also complex.

{% include layering/separate-layers.md %}

## Simple Layering Mode

If you do not need to use multiple regions or accounts layers, you can use simple layering mode.

config/app.rb

```ruby
Lono.configure do |config|
  config.layering.mode = "simple"
end
```

It'll look like this.

    app/blueprints/demo/config/params.env
    app/blueprints/demo/config/params/base.env
    app/blueprints/demo/config/params/dev.env
    config/blueprints/demo/params.env
    config/blueprints/demo/params/base.env
    config/blueprints/demo/params/dev.env

## Useful With

Showing layers to debug them is particularly useful when using:

* [App Layering]({% link _docs/layering/app.md %})
* [Custom Layering]({% link _docs/layering/custom.md %})
