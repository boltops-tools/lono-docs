---
title: More
---

Here are some more docs

{% assign docs = site.docs | where: "categories","more" | sort:"order" %}
{% for doc in docs -%}
* [{{ doc.title }}]({{ doc.url }})
{% endfor %}
