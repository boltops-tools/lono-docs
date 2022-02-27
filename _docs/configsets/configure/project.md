---
title: Configure Configsets at the Project-Level
nav_text: Project
---

Project configsets can be added at the lono project-level.

## Specifying Configsets

Here's how you specify which configsets you want a blueprint to use. Example:

config/blueprints/ec2/configsets.rb:

```ruby
configset("httpd", resource: "Instance")
```

This configuration tells Lono to add the `http` configset code to the compiled template in `output/ec2/template.yml`.  Notice, how you do not have to edit the `app/blueprints/ec2/template.rb` code. This is why the configset is reusable, you can selectively control which configset you want Lono to add to the blueprint's template.

## Configset Variables

If the configset has [configurable variables]({% link _docs/configsets/variables.md %}#user-custom-configset-variables), you can configure them like so:

config/blueprints/ec2/configsets/vars/httpd.rb

```ruby
@html = "some example html"
```

{% include configsets/cfn-init.md %}
