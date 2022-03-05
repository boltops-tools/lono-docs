---
title: lono seed
reference: true
---

## Usage

    lono seed BLUEPRINT

## Description

Builds starter configs for a blueprint.

## Example

    $ lono seed demo
    Creating starter config files for ec2
          create  config/blueprints/ec2/params/dev.txt
          create  config/blueprints/ec2/vars/dev.rb

To create the files in the top-level app folder

    $ lono seed ec2 --where app
    Creating starter config files for ec2
          create  app/blueprints/ec2/config/params/dev.txt
          create  app/blueprints/ec2/config/vars/dev.rb
    $

You can also set the default where option with

config/app.rb

```ruby
Lono.configure do |config|
    config.seed.where = "app"
end
```


## Options

```
    [--param=PARAM]        # override convention and specify the param file to use
-f, [--force]              # Overwrite files that already exist
-s, [--skip], [--no-skip]  # Skip files that already exist
    [--where=WHERE]        # Where to create file, you specify the top-level folder. Possible values: app, config, vendor. Defaults to config
```

