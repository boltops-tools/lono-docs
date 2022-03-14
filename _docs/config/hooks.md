---
title: Lifecycle Hooks
category: config
order: 5
---

Lono supports a variety of hooks. They can be used to customize and finely control the lifecycle process.

## Hook Levels

There are 2 hook types that operate at different levels:

1. **Project-level**: These hooks operate at the Lono project level. These hooks run on all stacks. They are defined in the root of the Lono project in the `config/hooks` folder. Project-level hooks run before blueprint or module level hooks.
2. **Blueprint-level**: These hooks operate at the blueprint level. They are defined in the blueprint folder. For example: `app/stacks/demo/config/hooks`. These hooks only run for that specific blueprint.

There are several types of hooks, so you may be unsure which to use. When in doubt, use the blueprint-level hooks. You probably want hooks to fire when deploying a specific blueprint only.

## Hook Docs

{% assign docs = site.docs | where: "categories","hooks" | sort:"order" %}
{% for doc in docs -%}
* [{{ doc.title }}]({{ doc.url }})
{% endfor %}
