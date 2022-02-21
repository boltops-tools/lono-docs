---
title: Layering
---

Lono supports a concept called layering.  This is useful for building different environments with the same CloudFormation template. For example, separate dev and prod environments.  Most of the infrastructure code is the same except for a few parts that require specific environment overrides.  Lono's layering ability makes this a simple task.

## Docs

{% assign docs = site.docs | where: "categories","layering" | sort: "order" %}
{% for doc in docs -%}
* [{{ doc.title }}]({{ doc.url }})
{% endfor %}
