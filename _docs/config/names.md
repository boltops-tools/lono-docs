---
title: Stack Name
nav_text: Stack Name
category: config
order: 7
---

You probably noticed that the stack names automatically have LONO_ENV added to the blueprint name. Example:

Command | CloudFormation Stack Name
---|---
LONO_ENV=dev lono up demo | demo-dev

## Customizing

You can customize the stack naming pattern with `config.names.stack`.

config/app.rb

```Ruby
Lono.configure do |config|
  config.names.stack = ":APP-:BLUEPRINT-:ENV"
end
```

Lono expands the pattern and replaces it with actual values.

## LONO_APP

The stack name will also include `LONO_APP` when set. Example:

Command | CloudFormation Stack Name
---|---
LONO_APP=app1 LONO_ENV=dev lono up demo | app1-demo-dev

## Clean Behavior

* Lono will clean the string from consecutive dashes. IE: `--` => `-`.  This allows `LONO_APP` to not be set.
* Starting and trailing dashes will be removed to keep the stack name clean.
* Underscores are replaced by dashes since only dashes are allowed in CloudFormation stack names.

{% include config/reference/header.md %}
{% include config/reference/names.md %}
{% include config/reference/footer.md %}
