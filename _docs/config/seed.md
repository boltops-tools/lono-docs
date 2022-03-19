---
title: Lono Seed
nav_text: Seed
category: config
order: 98
---

The `lono seed` command creates starter config params and vars files.

* Starter params are inferred from template parameters definition itself.
* Starter vars are determined by the blueprint's `seed/vars` files, written by the [author]({% link _docs/config/seed/authoring.md %}).

## Usage

The general form is:

    lono seed BLUEPRINT

## Examples

    $ lono seed vpc
          create  config/blueprints/vpc/params/dev.env
          create  config/blueprints/vpc/vars/dev.rb

config/blueprints/vpc/params/dev.env

    DomainName=dev.local # (required)
    VpcName=dev-vpc # (required)
    # EnableFlowLog=true⏎

config/blueprints/vpc/vars/dev.rb

```ruby
@vpc_cidr = "10.20.0.0/16"
@subnets = [
  {name: "PrivateApp1",  cidr: "10.20.0.0/19"},   # 8,192 hosts
  {name: "PrivateData1", cidr: "10.20.32.0/20"},  # 4,096 hosts
  {name: "Public1",      cidr: "10.20.48.0/20"},  # 4,096 hosts
]
```

To create starter tfvars file for a different environment, use `LONO_ENV`. Example:

    $ LONO_ENV=prod lono seed vpc
          create  config/blueprints/vpc/params/prod.env
          create  config/blueprints/vpc/vars/prod.rb

## Where Option

By default, the `seed` command generates starter config files to the `config/blueprints` folder. IE:

    $ lono seed vpc
          create  config/blueprints/vpc/params/dev.env
          create  config/blueprints/vpc/vars/dev.rb

You can adjust this behavior by using the `--where` option. Example:

    $ lono seed vpc --where app
          create  app/blueprints/vpc/config/params/dev.env
          create  app/blueprints/vpc/config/vars/dev.rb

Thanks to layering, either location works. For more details refer to [Full Layering Docs]({% link _docs/layering/full.md %}).
