---
title: Configset Structure
nav_text: Structure
categories: configsets
order: 3
---

## Basic Structure

The most basic configset structure simply has one file: either `configset.yml` or `configset.rb`.

Here's the structure with a YAML file.

    app/configsets/httpd
    └── configset.yml

Here's the structure with a Ruby file.

    app/configsets/httpd
    └── configset.rb

## Full Structure

Here's a fuller Lono configset structure, with a Ruby file as an example.

    app/configsets/httpd
    ├── configset.rb
    ├── helpers/
    └── vars.rb

The only require file is the `configset.{rb,yml}`. The rest of the folders and files are optional. Just add them when needed.

File | Description | Required?
--- | --- | ---
configset.rb | The configset code.  The top-level key should be [AWS::CloudFormation::Init](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-init.html). | required
helpers | Where you define custom helpers and extend the configset DSL. | optional
vars.rb | Default variables shipped with the configset. The variables can be overridden with [Configset Variables]({% link _docs/configsets/variables.md %}). | optional

## lono new configset

{% include configsets/lono-new-configset.md %}

{% include configsets/example.md %}
