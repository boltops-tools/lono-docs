---
title: App Layering
nav_text: App Layering
category: layering
order: 8
---

If `LONO_APP` is set, it activates App layering also. This is useful if you're using a central deploy pattern.

Here's an example with `LONO_APP=app1` and probably the most useful layers.

Params Layers

    config/blueprints/demo/params.txt
    config/blueprints/demo/params/base.txt
    config/blueprints/demo/params/dev.txt
    config/blueprints/demo/params/app1.txt
    config/blueprints/demo/params/app1/base.txt
    config/blueprints/demo/params/app1/dev.txt

To see the full app layers see [Debugging Layering Docs] where it shows you how to show the all layers.
