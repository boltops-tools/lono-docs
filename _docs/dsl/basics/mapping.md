---
title: Mapping
category: dsl-basics
desc: The optional Mappings section matches a key to a corresponding set of named
  values.
aws_text: Mappings
aws_link: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/mappings-section-structure.html
---

{{ page.desc }}

The `mapping` method maps to the CloudFormation Template Anatomy [{{ page.aws_text }}]({{ page.aws_link }}) section.

## Example Snippets

There are 2 forms for mapping.  Here are example snippets:

```ruby
# medium form
mapping("AmiMap",
  "ap-northeast-1": {Ami: "ami-084cb340923dc7101"},
  "ap-south-1":     {Ami: "ami-0d7805fed18723d71"},
)

# long form
mapping("ImageMap" => {
  "ap-northeast-1": {Ami: "ami-084cb340923dc7101"},
  "ap-south-1":     {Ami: "ami-0d7805fed18723d71"},
})
```

## Example Outputs

```yaml
Mappings:
  AmiMap:
    ap-northeast-1:
      Ami: ami-084cb340923dc7101
    ap-south-1:
      Ami: ami-0d7805fed18723d71
  ImageMap:
    ap-northeast-1:
      Ami: ami-084cb340923dc7101
    ap-south-1:
      Ami: ami-0d7805fed18723d71
```

## find_in_map method

The `mapping` method is used in conjuction with the [find_in_map]({% link _docs/dsl/intrinsic-functions/find_in_map.md %}) method.

{% include back_to/dsl-basics.md %}


