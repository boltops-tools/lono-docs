---
title: lono cfn download
reference: true
---

## Usage

    lono cfn download BLUEPRINT

## Description

Download CloudFormation template from existing blueprint.

## Examples

    lono cfn download demo


## Options

```
[--rollback], [--no-rollback]   # rollback
[--capabilities=one two three]  # iam capabilities. Ex: CAPABILITY_IAM, CAPABILITY_NAMED_IAM
[--iam], [--no-iam]             # Shortcut for common IAM capabilities: CAPABILITY_IAM, CAPABILITY_NAMED_IAM
[--name=NAME]                   # Name you want to save the template as. Default: existing stack name.
[--source=SOURCE]               # url or path to file with template
```

