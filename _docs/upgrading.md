---
title: Upgrading
---

If you're upgrading Lono, these upgrading docs may help.

## Summary

The following table summarizes the releases and upgrade paths.

Version | Notes
--- | ---
8.0 | Major structural changes. See: [Version 8 Upgrading Docs]({% link _docs/upgrading/version8.md %}).
7.0 | Project structural change: project blueprints moved from `blueprints` to `app/blueprints`.
5.0 | Major project structural changes to introduce blueprints concept.
4.2 | Change settings.yml structure.
4.0 | Major project structural changes to better organize app folder.

## Versions

<ul>
{% assign docs = site.docs | where: "categories","upgrading" | sort: "order" %}
{% for doc in docs -%}
  <li><a href='{{doc.url}}'>{{doc.title}}</a></li>
{% endfor %}
</ul>
