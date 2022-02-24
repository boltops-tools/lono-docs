---
title: Blueprint-Level Configsets
nav_text: Blueprint
---

Blueprint prepackage configsets themselves.

## Example

Blueprint specify configsets it wants to use in its `configsets.rb` file. Example:

app/blueprints/ec2/configsets.rb:

```ruby
configset("httpd", resource: "Instance")
```

This means the ec2 blueprint will use the `httpd` configset to install and run the httpd server.
