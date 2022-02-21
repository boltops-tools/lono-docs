---
title: Config
---

The `config` folder is where you can configure settings for the framework and blueprint configs like [params]({% link _docs/config/params.md %}) and [variables]({% link _docs/config/variables.md %}).

## Docs

{% assign docs = site.docs | where: "categories","config" | sort: "order" %}
{% for doc in docs -%}
  * [{{ doc.title }}]({{ doc.url }})
{% endfor %}
