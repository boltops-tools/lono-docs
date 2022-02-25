---
title: Custom Blueprint Helpers
nav_text: Blueprint
categories: custom-helpers
order: 1
---

Custom blueprint helpers are scoped to the blueprint. They live in the specific blueprint folder like `app/blueprints/demo`. For example:

    app/blueprints/demo/helpers/custom_helper.rb

They are only available to the specific blueprint. They can override Lono core built-in helpers and project-level helpers.

{% include helpers/blueprint-example.md %}
