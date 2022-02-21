---
title: Generators
---

## Docs

{% assign docs = site.docs | where: "categories","generators" | sort: "order" %}
{% for doc in docs -%}
  * [{{ doc.title }}]({{ doc.url }})
{% endfor %}

Lono ships with a few generators to help you get building quickly. The common ones.

    lono new blueprint NAME   # Generates new blueprint
    lono new project NAME     # Generates new project

Here are some additional generators:

    lono new configset NAME                           # Generates new configset
    lono new extension NAME                           # Generates new extension
    lono new helper --name NAME --blueprint BLUEPRINT # Generates new helper
    lono new shim                                     # Generates new shim

Here's a cheatsheet for generators. Refer to the cli reference for more docs: [lono new]({% link _reference/lono-new.md %})

We'll cover the common generators next.
