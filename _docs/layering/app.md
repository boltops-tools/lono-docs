---
title: App and Role Layering
nav_text: App Layering
category: layering
order: 5
---

## Concept

Lono also has the concept of `LONO_APP` and `LONO_ROLE` layering.  This is helpful when using Lono and CloudFormation to deploy app-central resources. Some possible examples are AWS CodeBuild and CodePipeline resources. When `LONO_APP` is set, app-scoped layers are activated. And when `LONO_ROLE` is set, role-scoped layers are also activated.

## Why the App and Role Layers?

First, Lono is a CloudFormation framework. As such, it is mainly used to provision AWS Cloud infrastructure.  Infrastructure can be sometimes **env-centric** or **app-centric**, though. Some examples:

* **env-centric**: VPC networks, ECS clusters, EKS clusters. Can also be thought of as **infra-centric**.
* **app-centric**: CodeBuild projects, CodePipeline pipelines. These resources can be specific to apps.

Multiple apps typically share env-centric infrastructure components. App-centric infrastructure focuses on specific apps.

With app-centric infrastructure, one option is to create separate blueprints. Example:

    app/blueprints/app1
    app/blueprints/app2
    # and
    lono up app1
    lono up app2

Or you can create a "standard" app blueprint and then override configurations with the app-scoped layers. Example:

    app/blueprints/app
    # and
    LONO_APP=1 lono up app
    LONO_APP=2 lono up app

Essentially, the **same** blueprint is reuse for multiple apps. It's DRY. However, if an app strays too far away from the "standard" blueprint code, it may make sense to create a new dedicated blueprint.

## Stick to a Few

Since layering is so powerful, you want to choose a few layers that make sense for your team and stick to them. First set `LONO_APP` and `LONO_ROLE`.

    export LONO_APP=app1
    export LONO_ROLE=deploy

Here are some layers that you can use now.

    config/blueprints/demo/params/app1/base.env
    config/blueprints/demo/params/app1/dev.env
    config/blueprints/demo/params/app1/deploy/base.env
    config/blueprints/demo/params/app1/deploy/dev.env

Shown as a tree

    config/blueprints/demo/params/
    └── app1
        ├── base.env
        │── dev.env
        └── deploy
            ├── base.env
            └── dev.env

## Seeing Layers Clearly

{% include layering/config-layering-show.md %}

    $ export LONO_APP=app1
    $ export LONO_ROLE=deploy
    $ lono build demo
    Building parameters
        config/blueprints/demo/params/app1/base.env
        config/blueprints/demo/params/app1/dev.env
        config/blueprints/demo/params/app1/deploy/base.env
        config/blueprints/demo/params/app1/deploy/dev.env
        output/demo/params.json

{% include layering/found-layers-note.md %}
