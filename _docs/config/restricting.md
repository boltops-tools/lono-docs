---
title: Restricting Deployment
nav_text: Restricting
category: config
order: 88
---

Lono can deploy to any region and environment by default.  This power may be too much for some folks who would prefer more restrictions.  You can configure which regions and envs that stacks can be deployed to with Lono settings. Below are links covering how to achieve this.

{% assign docs = site.docs | where: "categories","restricting" | sort:"order" %}
{% for doc in docs -%}
* [{{ doc.title }}]({{ doc.url }})
{% endfor %}
