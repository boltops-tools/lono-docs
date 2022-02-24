---
title: Lookups
nav_text: Lookups
categories: blueprint
order: 2
---

Lono blueprints can be in different locations. Lono searches the locations, similar to how `LOAD_PATH` works. The locations are:

    app/blueprints
    vendor/blueprints

## Examples

If you only have:

    app/blueprints/demo

So `lono up` will use the blueprint in the `app/blueprints` folder.

    lono up demo # uses app/blueprints/demo

If you only have:

    vendor/blueprints/demo

So `lono up` will use the blueprint in the `vendor/blueprints` folder.

    lono up demo # uses vendor/blueprints/demo

If you have both:

    app/blueprints/demo
    vendor/blueprints/demo

The `app/blueprints` folder takes higher precedence.

    lono up demo # uses app/blueprints/demo

## Why Vendor?

The vendor folder allows the reuse of 3rd party blueprints. It works with the [Lonofile]({% link _docs/lonofile.md %}). At the same time, the source code is there and easily available for debugging.
