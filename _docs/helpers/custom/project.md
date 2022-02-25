---
title: Custom Project Helpers
nav_text: Project
categories: custom-helpers
order: 2
---

Project-level helpers are scope to the entire Lono project. They live in the lono `app/helpers` folder. For example:

    app/helpers/custom/custom_helper.rb

They are available project-wide to **all** blueprints. Blueprints that use project-level helpers are dependent on those helpers. As such, they are not as indepedent. Project-level helpers are useful though, particularly if you have helper definitions that are used by multiple blueprints.

{% include helpers/project-example.md %}
