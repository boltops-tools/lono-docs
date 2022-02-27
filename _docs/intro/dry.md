---
title: 'DRY: Reusable Templates'
nav_text: DRY
categories: intro
order: 5
---

Lono design allows you to reuse CloudFormation templates.  A key is the separation of config and template code in a structured and organized way.

## Configs

Here's an example config structure:

    config/blueprints
    └── demo
        └── params
            ├── dev.txt
            └── prod.txt

Notice how there are different `dev` and `prod` config files. This structure allows you to create different environments with the same CloudFormation template.  Learn more: [Layering]({% link _docs/layering.md %}).

## Blueprints

The CloudFormation code itself lives in the blueprints folder.

    app/blueprints
    └── demo

Docs: [Blueprints]({% link _docs/blueprints.md %}).

## Summary

With this structure, it DRYs up your code by allowing you to reuse the same CloudFormation templates.
