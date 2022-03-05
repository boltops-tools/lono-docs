---
title: lono helper blueprint
reference: true
---

## Usage

    lono helper blueprint HELPER_NAME --blueprint --blueprint=BLUEPRINT

## Description

Generates new blueprint helper

## Example

The default helper name is `custom`.

    $ lono new helper blueprint --blueprint demo
    => Generating custom_helper.rb
          create  app/blueprints/demo/helpers
          create  app/blueprints/demo/helpers/custom_helper.rb


You can override the helper name with the first argument.

    $ lono new helper blueprint vars --blueprint demo
    => Generating vars_helper.rb
          create  app/blueprints/demo/helpers
          create  app/blueprints/demo/helpers/vars_helper.rb
    $


## Options

```
[--force]              # Bypass overwrite are you sure prompt for existing files
--blueprint=BLUEPRINT  # Blueprint name
```

