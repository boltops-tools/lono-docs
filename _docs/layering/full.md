---
title: Full Layering
nav_text: Full Layering
category: layering
order: 4
---

The [Basic layering]({% link _docs/layering/basics.md %}) docs focuses on providing a gentle introduction to layering. This document covers layering in more detail.

## Stick to a Few

Since layering is so powerful, you want to choose a few layers that make sense for your team and stick to them. Here's an example:

Vars

    config/blueprints/demo/vars/base.rb
    config/blueprints/demo/vars/dev.rb

Params

    config/blueprints/demo/params/base.env
    config/blueprints/demo/params/dev.env

Shown as a tree:

    config/blueprints/demo
    ├── params
    │   ├── base.env
    │   └── dev.env
    └── vars
        ├── base.rb
        └── dev.rb

## Seeing Layers Clearly

{% include layering/config-layering-show.md %}

    $ lono build demo
    Building template
        config/blueprints/demo/vars/base.rb
        config/blueprints/demo/vars/dev.rb
        output/demo/template.yml
    Building parameters
        config/blueprints/demo/params/base.env
        config/blueprints/demo/params/dev.env
        output/demo/params.json

{% include layering/found-layers-note.md %}
