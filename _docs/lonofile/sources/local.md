---
title: Local paths
nav_text: Local
categories: sources
order: 5
---

## Example

Lonofile

```ruby
blueprint "local1", source: "/home/ec2-user/environment/downloads/demo-blueprint"
blueprint "local2", source: "./demo-blueprint"
blueprint "local3", source: "~/environment/infra-lonofile/demo-blueprint"
```

Running:

    lono bundle

Will download blueprints to:

    vendor/blueprints/local1
    vendor/blueprints/local2
    vendor/blueprints/local3
