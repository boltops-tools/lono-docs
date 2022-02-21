---
title: Lonofile Version Locking
---

Lono provides a lot of control over version locking.

## Example

Here's a `Lonofile` example with the different version options:

```ruby
# GitHub repo
blueprint "example1", source: "boltops-tools/terraform-aws-s3", version: "master"
blueprint "example2", source: "boltops-tools/terraform-aws-s3", branch: "master"
blueprint "example3", source: "boltops-tools/terraform-aws-s3", ref: "3a414a39"
blueprint "example4", source: "boltops-tools/terraform-aws-s3", sha: "c1d04816"
blueprint "example5", source: "boltops-tools/terraform-aws-s3", tag: "v0.1.0"
```

Run `lono bundle` to download the blueprints:

    $ lono bundle
    Bundling with Lonofile...
    Exporting vendor/blueprints/example1
    Exporting vendor/blueprints/example2
    Exporting vendor/blueprints/example3
    Exporting vendor/blueprints/example4
    Exporting vendor/blueprints/example5

To list the blueprints:

    $ lono list --type blueprint
    vendor/blueprints/example1
    vendor/blueprints/example2
    vendor/blueprints/example3
    vendor/blueprints/example4
    vendor/blueprints/example5

A `Lonofile.lock` is also generated to lock the versions. For strict versions like `tag: "v0.1.0"` the versions are locked as-is. For "loose" versions like `branch: "master"` the latest current version is snapshotted.  You can update these versions with:

    lono bundle update

This updates the `Lonofile.lock` versions.

