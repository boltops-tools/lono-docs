---
title: Full Layering
nav_text: Full Layering
category: layering
order: 4
---

The [Basic layering]({% link _docs/layering/basics.md %}) docs focuses on providing a gentle introduction to layering. This document covers the full power of layering.

## Full Layering with LONO_ENV

As covered in [Basic layering]({% link _docs/layering/basics.md %}), layering generally work the same for params and variables files. They use different folders. Params have a `.txt` extension and vars have a `.rb` extension.

To explain advanced and full layering we'll use params and a concrete example where `LONO_ENV=dev`.

Name | Example
--- | --- | ---
app params | app/blueprints/demo/config/params/{base,dev}.txt
app region | app/blueprints/demo/config/params/us-west-2/{base,dev}.txt
app account | app/blueprints/demo/config/params/111111111/{base,dev}.txt
app account/region | app/blueprints/demo/config/params/111111111/us-west-2/{base,dev}.txt
config params | config/blueprints/demo/params/{base,dev}.txt
config region | config/blueprints/demo/params/us-west-2/{base,dev}.txt
config account | config/blueprints/demo/params/111111111/{base,dev}.txt
config account/region | config/blueprints/demo/params/111111111/us-west-2/{base,dev}.txt

Here's a specific example: `app/blueprints/demo/config/params/dev.txt`. The layers are processed in order and override previous values.  So `config/blueprints/demo/params/111111111/us-west-2/dev.txt` takes the highest precedence in this case.

## Why Separate Config Folder?

You can have your params values defined in the `app/blueprints/demo` itself or separate them from the blueprint and define them at the project-level in `config/blueprints` files.

Generally, it is recommended to define the custom params and variables separately in `config/blueprints` project-level files so the blueprints can be reusable.

## Full Layering with LONO_APP

Additionally, When LONO_APP is set, app-scoped layers are also considered. Given `LONO_APP=app1` is set, here are the processed layers. We'll cover the top-level `config/blueprints` folders only to help explain.

Within the `config/blueprints/demo` folder:

Name | Example
--- | --- | ---
params | params/{base,ENV}.txt | params/{base,dev}.txt
region | params/REGION/{base,ENV}.txt | params/us-west-2/{base,dev}.txt
account | params/ACCOUNT/{base,ENV}.txt | params/111111111/{base,dev}.txt
account/region | params/ACCOUNT/REGION/{base,ENV}.txt | params/111111111/us-west-2/{base,dev}.txt
app | params/APP/{base,ENV}.txt | params/app1/{base,dev}.txt
app region | params/APP/REGION/{base,ENV}.txt | params/app1/us-west-2/{base,dev}.txt
app account | params/APP/ACCOUNT/{base,ENV}.txt | params/app1/111111111/{base,dev}.txt
app account/region | params/APP/ACCOUNT/REGION/{base,ENV}.txt | params/app1/111111111/us-west-2/{base,dev}.txt

To be specific, here's an example full path: `config/blueprints/demo/params/app1/dev.txt`

The top-level `app/blueprints` folder processing works the same way. Since `config/blueprints/demo` folders get processed after the `app/blueprints/demo` folders, they override previous settings and take higher precedence. Ultimately, your user custom settings always win.

Note: The folder name with extension is also a considered layer. IE: `params.txt`, `params/app1.txt`, etc. They are not shown for simplicity. Also, see [Debugging Layering]({% link _docs/layering/debugging.md %}) for how to see all the considered layers.

## Why the App-Scoped Layers?

Here are some thoughts to help explain why Lono also has app-scoped layers. It is based on real-world usage.

First, Lono is a CloudFormation framework. As such, it is mainly used to provision AWS Cloud infrastructure.  Infrastructure can be sometimes env-centric or app-centric. To help explain, here are some examples:

* **env-centric**: VPC networks, ECS clusters, EKS clusters.
* **app-centric**: CodeBuild projects, CodePipeline pipelines.

Env-centric infrastructure components are typically shared by multiple apps. App-centric infrastructure is usually more focused on specific apps.

With app-centric infrastructure, one option is to create completely separate blueprints. Example:

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

We call this the "Central Standard App Deployment Pattern". It is easier to **standardize** app-focused CloudFormation infrastructure resources with the central app pattern, as the same blueprint code is used. There's less duplication. Of course, if the specific apps stray too far away from the "standard" app, it may make sense to create a new dedicated blueprint.
