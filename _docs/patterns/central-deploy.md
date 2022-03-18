---
title: Central Deploye Pattern
nav_text: Central Deploye
categories: patterns
order: 1
---

Lono can be use as either an app-centric or infra-centric tool.

* **app-centric**: Each app repo has it's own `.ufo` settings files. This is useful if your applications are very differently setup.
* **infra-centric**: Each app repo has pretty much the same `.ufo` settings files. This is useful if your applications are very similarly set up.

An infra-centric approach generally makes sense for shared resources by multiple applications. VPC Networks, ECS Clusters, and EKS Clusters are good examples

## Setup

    app/blueprints/vpc
    app/blueprints/ecs
    app/blueprints/eks

    https://github.com/org/app1
    https://github.com/org/app2

You then also have a

    https://github.com/org/ufo-central

You can copy the `ufo-central` repo into the app repo folder with the [ufo central update]() command like so:

    cd app1
    ufo central update

You'll end up with something like this:

    app1/.ufo
    app2/.ufo

Then to deploy different app level settings.

For app1:

    cd app1
    export UFO_APP=app1
    ufo ship

And for app2:

    cd app1
    export UFO_APP=app2
    ufo ship

Also check out: [Layering]({% link _docs/layering.md %}).

The central deployer approach is removes duplication of the ufo config files between projects. Leveraging app-level overrides provide a great degree of control.

If the settings start to diverge too much, then it probably makes sense to use separate `.ufo` files in that app specific repo.
