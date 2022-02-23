---
title: Lonofile
---

The Lonofile allows you to manage and reuse lono components like blueprints, configsets, and extensions. You centrally define, manage, and update them. Add them to `Lonofile`:

Lonofile

```ruby
blueprint "ec2",   source: "git@github.com:boltops-tools/ec2_blueprint"
configset "httpd", source: "git@github.com:boltops-tools/httpd_configset"
extension "ec2",   source: "git@github.com:boltops-tools/ec2_extension"
```

{% include lonofile/usage.md %}
