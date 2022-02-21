---
title: Authoring Seed Files
nav_text: Authoring
order: 2
---

The `lono seed` command creates starter config params and vars files. For blueprint authors, it's helpful to know how `lono seed` generates these starter files.

## Params Starter Files

Parameter starter values are inferred from the template definition itself. You don't have to do anything extra. For example:

```ruby
parameter("Subnets", Description: "Subnets in the VPC. Example: subnet-111,subnet-222 # at least 2 subnets required")
```

The parameter defintion is enough for the [lono seed](https://lono.cloud/reference/lono-seed/) to produce:

    Subnets=subnet-111,subnet-222 # at least 2 subnets required

Additionally, example values are gleaned from the `Description` attribute.  Anything after the `IE:` or `Example:` text is used as the starter parameter value.  The code self-documents the starter parameters!

## Vars Starter Files: Basics

Vars starter files are based on the `seed/vars` files provided in the blueprint. Here's a simple example:

    app/blueprints/vpc/seed
    └── vars
        ├── dev.rb
        └── prod.rb

app/blueprints/vpc/seed/vars/dev.rb

```ruby
@vpc_cidr = "10.20.0.0/16"
@subnets = [
  {name: "PrivateApp1",  cidr: "10.20.0.0/19"},   # 8,192 hosts
  {name: "PrivateData1", cidr: "10.20.32.0/20"},  # 4,096 hosts
  {name: "Public1",      cidr: "10.20.48.0/20"},  # 4,096 hosts
]
```

app/blueprints/vpc/seed/vars/prod.rb

```ruby
@vpc_cidr = "10.22.0.0/16"
@subnets = [
  {name: "PrivateApp1",  cidr: "10.22.0.0/19"},   # 8,192 hosts
  {name: "PrivateData1", cidr: "10.22.32.0/20"},  # 4,096 hosts
  {name: "Public1",      cidr: "10.22.48.0/20"},  # 4,096 hosts
]
```

## Vars Starter Files: Advanced Dynamic Templating

Var starter files can also be template based.  Adding a `.tt` extension the files results the files being processed by ERB templating. Example:

app/blueprints/demo/seed/vars/dev.rb.tt

```ruby
@var1 = "<%= Lono.env %>"
```

Additionally, if you want the filename itself to be named based on template variables, wrap the filename with `%` signs. Example:

app/blueprints/demo/seed/vars/%env%.rb.tt

```ruby
@var1 = "<%= Lono.env %>"
```
