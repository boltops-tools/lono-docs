---
title: Blueprints
---

Lono blueprints encapsulate the code used to build CloudFormation templates and infrastructure resources.  Essentially, Lono blueprints packaged up the template in a organized and reusable way, keeping the code [DRY]({% link _docs/intro/dry.md %}). Blueprints are what you'll mostly work with and can live in `app/blueprints`.

{% include blueprint/structure.md %}

## Blueprint Generator

To create a new blueprint you can use:

    lono new blueprint demo

This creates a `app/blueprints/demo` folder in your lono project with a starter structure.

To list the project's blueprints:

    lono list

## Lonofile

Blueprints can also be loaded with the [Lonofile]({% link _docs/lonofile.md %}).  Example:

Lonofile

```ruby
blueprint "ec2", git: "boltopspro/ec2-blueprint"
blueprint "vpc", git: "boltopspro/vpc-blueprint"
```
