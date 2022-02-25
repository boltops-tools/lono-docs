---
title: Blueprint-Level Configsets
nav_text: Blueprint
---

Blueprint can preconfigure configsets themselves. Blueprint specify configsets with `configsets.rb`. Example:

app/blueprints/ec2/configsets.rb:

```ruby
configset("httpd", resource: "Instance")
```

This means the ec2 blueprint will be shipped to use the `httpd` configset to install and run the httpd server.

## Configset Default Variables

Configsets specified within blueprints can also set default variables in their `vars.rb` file.  Example:

app/blueprints/ec2/configsets/vars/httpd.rb:

```ruby
@html = "default example html"
```

This can be overriden by the user at the project-level with `config/blueprints/ec2/configsets/vars/httpd.rb`. See: [Project-Level Configset Variables]({% link _docs/configsets/using/project.md %}#configset-variables).

{% include configsets/cfn-init.md %}
