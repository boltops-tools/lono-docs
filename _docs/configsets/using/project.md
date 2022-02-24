---
title: Project-Level Configsets
nav_text: Project
---

Project configsets are added at the lono project-level. Example:

config/blueprints/ec2/configsets.rb:

```ruby
configset("httpd", resource: "Instance")
```

This configuration tells Lono to add the `http` configset code to the compiled template in `output/ec2/template.yml`.  Notice, how you're not making any adjustmennts to the `app/blueprints/ec2` code. This is why the configset is reusable, you can selectively control which configset you want Lono to add to the blueprint's template.

{% include configsets/cfn-init.md %}
