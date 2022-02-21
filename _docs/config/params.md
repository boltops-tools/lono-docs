---
title: Params
nav_text: Params
category: config
order: 3
---

CloudFormation parameters allow you to create different environments with the same template code. Lono params simplify this process by providing an env-like file syntax.

## Structure

The `config` files are located at `config/blueprints/BLUEPRINT/params`.  Example:

    config/blueprints
    └── demo
        └── params
            ├── dev.txt
            └── prod.txt

## Examples

Lono allows you to set parameters in a simple `KEY=VALUE` format commonly found in env files.  This format is less prone to human error than the AWS more verbose parameter file format.  When [lono build](/reference/lono-build/) runs it processes the files in `config/blueprints/BLUEPRINT/params` folders and outputs the AWS JSON format file in `output/BLUEPRINT/params` folder.  Here's an example:

config/blueprints/demo/params/dev.txt

    KeyName=default
    InstanceType=t2.micro

This results in:

```json
[
  {
    "ParameterKey": "InstanceType",
    "ParameterValue": "t2.micro"
  },
  {
    "ParameterKey": "KeyName",
    "ParameterValue": "default"
  }
]
```

These files can directly be used to launch the CloudFormation stack with the `aws cloudformation` CLI tool manually. Though, the `lono up` command automates this for you. For example, running `lono up BLUEPRINT` will automatically build the param file and use it when deploying the stack.

## ERB Support and SSM Helper

Parameters files support ERB evaluation.  This allows you to  use the [ssm helper method](https://github.com/boltops-tools/lono/blob/master/lib/lono/template/context/helpers.rb) to substitute secrets from SSM parameter store.  This avoids committing secret information to your repo. Example:

config/blueprints/demo/params/dev.txt

    KeyName=<%= ssm("/#{Lono.env}/key_name") %>
    InstanceType=t2.micro

Here's an example of storing an SSM parameter:

    aws ssm put-parameter --name /dev/key_name --value demo-key-pair --type SecureString

To confirm that parameter is stored:

     aws ssm get-parameter --name /dev/key_name --with-decryption

## Variables Substitution

[Variables]({% link _docs/config/variables.md %}) are also available in the params file.  Here's an example:

config/blueprints/demo/vars/base.rb

    @ami = "ami-12345"

config/blueprints/demo/params/base.rb

    Ami=<%= @ami %>

Will produce:

output/demo/params/mystack.json

```json
[
  {
    "ParameterKey": "Ami",
    "ParameterValue": "ami-12345"
  }
]
```

## Layering Support

Lono params support layering which is covered in [Layering Support]({% link _docs/layering.md %}). This allows you to create different environments with the same CloudFormation template.
