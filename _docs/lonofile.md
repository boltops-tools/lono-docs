---
title: Lonofile
---

The Lonofile allows you to manage and reuse lono components like blueprints, configsets, and helpers. You centrally define, manage, and update them. Add them to `Lonofile`:

Lonofile

```ruby
blueprint "ec2",   source: "boltops-tools/ec2-blueprint"
configset "httpd", source: "boltops-tools/httpd-configset"
helper    "ec2",   source: "boltops-tools/ec2-helper"
```

{% include lonofile/usage.md %}
