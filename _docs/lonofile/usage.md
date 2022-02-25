---
title: Lonofile Usage
---

## Example

Here's an example `Lonofile`.

```ruby
blueprint "ec2",   source: "boltops-tools/ec2-blueprint"
configset "httpd", source: "boltops-tools/httpd-configset"
helper    "ec2",   source: "boltops-tools/ec2-extension"
```

**Options Docs**:

* [Component-level options]({% link _docs/lonofile/options.md %}#1-component-level): : These options apply at the component-level, so they specifically affect each component only.
* [Lonofile-level options]({% link _docs/lonofile/options.md %}#2-Lonofile-level): These options apply globally and affect the entire Lonofile.

**Additional Docs**:

* [Version Locking Docs]({% link _docs/lonofile/version-locking.md %}): Everything you may want to know about version locking.

## Install

When you run:

    lono bundle

The components in `Lonofile` are downloaded to the `vendor` folder.

A `Lonofile.lock` file is generated to lock component versions. You can then check in the lockfile into version control.  Other members on your team running `lono bundle` will download the **exact** same versions as you.

{% include lonofile/usage.md %}

## Updating

To update the `Lonofile.lock` with the latest versions.

    lono bundle update

You can also selectively update multiple components.

    lono bundle update blueprint1 configset2 extension3

## Listing

You can list the components that installed from the `Lonofile` with:

    $ lono bundle list
    Components included by Lonofile.lock

    +---------------+-----------+
    |     Name      |   Type    |
    +---------------+-----------+
    | asg-extension | extension |
    | httpd         | configset |
    | vpc           | blueprint |
    +---------------+-----------+

    Use `lono bundle info` to print more detailed information about a component

## Getting Info

You can get additional information about each bundled component with:

    $ lono bundle info vpc
    vpc:
        sha: f8c0f95008f64a25461d9ff88ebd3e5ae1d4c785
        source: git@github.com:boltopspro/vpc
        source_type: git
        type: blueprint
        url: git@github.com:boltopspro/vpc
