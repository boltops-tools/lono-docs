---
title: "Git: GitHub, Bitbucket, GitLab repositories"
nav_text: Git
categories: sources
order: 1
---

## Example

Lonofile

```ruby
blueprint "ec2",   source: "https://github.com/org/ec2-blueprint"
configset "httpd", source: "git@bitbucket.org:org/httpd-configset"
extension "asg",   source: "git@gitlab.com:org/asg-extension"
```

Running:

    lono bundle

Will download components to:

    vendor/blueprints/ec2
    vendor/configset/httpd
    vendor/extensions/asg

## Shorthand

GitHub is the default git source, so you can use shorthand notation:

```ruby
blueprint "ec2", source: "boltopspro/ec2-blueprint"
```

You can use an even shorter hand notation by setting the org:

```ruby
org "boltopspro"
blueprint "ec2", source: "ec2-blueprint" # inferred org
```
