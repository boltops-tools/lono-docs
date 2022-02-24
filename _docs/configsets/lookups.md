---
title: Lookups
nav_text: Lookups
categories: configsets
order: 15
---

Lono configsets can be in different locations. Lono searches the locations, similar to how `LOAD_PATH` works. The locations are:

    app/configsets
    vendor/configsets

## Examples

If you only have:

    app/configsets/httpd

Lono will use the configset defined in the `app/configsets` folder.

If you only have:

    vendor/configsets/httpd

Lono will use the configset in the `vendor/configsets` folder.

If you have both:

    app/configsets/httpd
    vendor/configsets/httpd

The `app/configsets` folder takes higher precedence.

## Why Vendor?

The vendor folder allows the reuse of 3rd party configsets. It works with the [Lonofile]({% link _docs/lonofile.md %}). At the same time, the source code is there and easily available for debugging.
