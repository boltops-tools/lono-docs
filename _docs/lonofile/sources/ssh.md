---
title: "SSH"
nav_text: SSH
categories: sources
order: 6
---

## Example

Lonofile

```ruby
blueprint "blueprint1", source: "ssh://user@host:repo"
blueprint "blueprint2", source: "ssh://user@host:relative/path/from/home/to/repo"
blueprint "blueprint3", source: "ssh://user@host/absolute/path/to/repo"
blueprint "blueprint4", source: "ssh://host:repo"
blueprint "blueprint5", source: "git::https://github.com/boltops-tools/terraform-aws-s3"
```

Running:

    lono bundle

Will download blueprints to:

    vendor/blueprints/blueprint1
    vendor/blueprints/blueprint2
    vendor/blueprints/blueprint3
    vendor/blueprints/blueprint4
    vendor/blueprints/blueprint5
