---
title: lono new helper
reference: true
---

## Usage

    lono new helper NAME

## Description

Generate new helper

## Blueprint Helpers

When the `--blueprint` option is used a blueprint helper is generated.

The default name is custom

    $ lono new helper --blueprint codebuild
          create  app/blueprints/codebuild/helpers/custom_helper.rb

Here's an example with a helper named vars.

    $ lono new helper vars --blueprint codebuild
          create  app/blueprints/codebuild/helpers/vars_helper.rb

## Project Helpers

When no `--blueprint` option is used a project helper is generated.

The default name is custom.

    $ lono new helper
          create  app/helpers/custom/custom_helper.rb

Here's an example with a helper named common.

    $ lono new helper common
          create  app/helpers/common/common_helper.rb


## Options

```
[--force]                # Bypass overwrite are you sure prompt for existing files
[--blueprint=BLUEPRINT]  # Blueprint name. Only use you want a blueprint helper. Otherwise a project helper is generated
```

