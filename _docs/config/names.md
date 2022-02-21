---
title: Stack Name
nav_text: Stack Name
category: config
order: 7
---

The default stack name will include `LONO_APP` and `LONO_ENV`. `LONO_APP` is only included when set. Examples:

Command | CloudFormation Stack Name
---|---
LONO_ENV=dev lono up demo | demo-dev
LONO_APP=app1 LONO_ENV=dev lono up demo | demo-app1-dev

## Customizing

You can customize the stack naming pattern with `config.names.stack`.

config/app.rb

```ruby
Lono.configure do |config|
  config.names.stack = ":BLUEPRINT-:APP-:ENV"
end
```

## Clean Behavior

* Lono will clean the string from consecutive dashes. IE: `--` => `-`.  This allows `LONO_APP` to not be set.
* Starting and trailing dashes will be removed to keep the stack name clean.
* Underscores are replaced by dashes since only dashes are allowed in CloudFormation stack names.
