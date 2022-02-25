---
title: Custom Helpers
nav_text: Custom
categories: helpers
order: 2
---

Defining custom helpers is a good way to simplify your code, remove duplication, and keep it organized. The custom helpers are first class citizens and have access to the same context and variables as [built-in DSL helpers]({% link _docs/helpers/builtin.md %}). There are 2 types of custom helpers you can create:

{% assign docs = site.docs | where: "categories","custom-helpers" | sort: "order" %}
{% for doc in docs -%}
* [{{ doc.title }}]({{ doc.url }})
{% endfor %}
