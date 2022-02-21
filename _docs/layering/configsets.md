---
title: Configset Layering
nav_text: Configsets
category: layering
order: 7
---

Configsets also support the concept of layering. Let's say you have the following configsets directory structure:

    config/blueprints/demo/configsets
    ├── base.rb
    ├── dev.rb
    └── prod.rb

In this case:

* `base.rb` is always evaluated.
* `dev.rb` or `prod.rb` is evaluated based on LONO_ENV.

Since configsets are a way to dynamically inject cfn-init scripts into the CloudFormation template, you might want to use it to configure differrent configsets for dev and prod environments.

config/blueprints/demo/configsets/base.rb:

```ruby
configset("cfn-hup", resource: "Instance")
```

config/blueprints/demo/configsets/prod.rb:

```ruby
configset("httpd", resource: "Instance")
```

Lono will always use the `cfn-hup` configset, but only the `httpd` for the prod environment.
