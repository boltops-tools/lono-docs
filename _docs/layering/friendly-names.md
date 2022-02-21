---
title: Friendly Names
nav_text: Friendly Names
category: layering
order: 6
---

You can configure a `layering.names` map to assign friendly names to the layer name.  Currently, namespace is supported. Example setup:

config/app.rb

```ruby
Lono.configure do |config|
  config.layering.names = {
    "111111111111" => "dev-account",
    "222222222222" => "prod-account",
  }
end
```

This maps the `111111111111` namespace to a friendly  name `dev-account`. So when you build or deploy it'll use the friendly name. Example:

    $ ls config/blueprints/demo/params/dev-account
    base.txt
    $ lono build demo

Without the mapping, the paths would look like so:

    $ ls config/blueprints/demo/params/111111111111
    base.tfvars
    $ lono build demo

Here's a useful command to check for the AWS account id.

    $ aws sts get-caller-identity
    {
        "UserId": "EXAMPLE16O4571EXAMPLE",
        "Account": "111111111111",
        "Arn": "arn:aws:iam::111111111111:user/tung"
    }
