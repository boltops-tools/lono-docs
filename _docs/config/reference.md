---
title: Reference
nav_text: Reference
category: config
order: 99
---

{% include config/reference/header.md %}
{% include config/reference/logging.md %}
{% include config/reference/names.md %}
plan.changeset | Whether or not to show a Change Set Diff when running `lono up`. Can be set to: true or false | true
plan.params | Whether or not to show a Parameters Diff when running `lono up`. Can be set to: true or false. | true
plan.template | Whether or not to show a Template Diff when running `lono up`. Can be set to: full, summary, or false. | summary
seed.where | Where to write the starter config files to. You specify the top-level folder. Possible values: config, app, vendor | config
up.capabilities | In some cases, you must explicitly acknowledge that your stack template contains certain capabilities in order for CloudFormation to create the stack. By default, the `lono up` command does not set any capabilities for security. You can set `config.up.capabilities = ["CAPABILITY_IAM", "CAPABILITY_NAMED_IAM", "CAPABILITY_AUTO_EXPAND"]` to generally bypass IAM capabilities prompts. You can also bypass prompts with the CLI `--iam` option. | nil
up.notification_arns | SNS topics to publish stack related events | nil
up.rollback | Rollback of the stack if stack creation failed | true
