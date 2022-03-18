---
title: Extra Layering
nav_text: Extra Layering
category: layering
order: 6
---

If you're setting the `LONO_EXTRA` env var to leverage the Lono.extra feature, it also activate an extra layer.

## Example

    export LONO_EXTRA=2

Vars

    config/blueprints/demo/vars/base.rb
    config/blueprints/demo/vars/dev.rb
    config/blueprints/demo/vars/dev-2.rb    <= extra layer

Params

    config/blueprints/demo/params/base.env
    config/blueprints/demo/params/dev.env
    config/blueprints/demo/params/dev-2.env <= extra layer

## Seeing Layers Clearly

{% include layering/config-layering-show.md %}

    $ lono build demo
    Building template
        config/blueprints/demo/vars/base.rb
        config/blueprints/demo/vars/dev.rb
        config/blueprints/demo/vars/dev-2.rb
        output/demo/template.yml
    Building parameters
        config/blueprints/demo/params/base.env
        config/blueprints/demo/params/dev.env
        config/blueprints/demo/params/dev-2.env
        output/demo/params.json

{% include layering/found-layers-note.md %}
