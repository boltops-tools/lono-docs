---
title: Configset Custom Helpers
nav_text: Custom
categories: configsets-helpers
order: 2
---

Helpers allow you to extend the Configset DSL.

## Example

Here's a simple example that will add a `yum` keyword.

helpers/yum_helper.rb

```ruby
module YumHelper
  def yum(*packages)
    list = packages.inject({}) { |result, p| result.merge(p => []) }
    package("yum", list)
  end
end
```

Now you can use like so:

```ruby
yum("tree", "vim")
```

And it'll generate something like this:

```yaml
---
AWS::CloudFormation::Init:
  configSets:
    default:
    - main
  main:
    packages:
      yum:
        tree: []
        vim: []
```

Both ERB and DSL from supports adding your own custom helpers.


