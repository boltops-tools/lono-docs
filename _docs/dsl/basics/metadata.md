---
title: Metadata
category: dsl-basics
desc: The optional Mappings section matches a key to a corresponding set of named
  values.
aws_text: Metadata
aws_link: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/metadata-section-structure.html
---

{{ page.desc }}

The `metadata` method maps to the CloudFormation Template Anatomy [{{ page.aws_text }}]({{ page.aws_link }}) section.

## Example Snippet

```ruby
metadata(
  Authors: { Description: "Tung Nguyen (tongueroo@gmail.com)" },
  License: "MIT"
)
```

## Example Outputs

```yaml
Metadata:
  Authors:
    Description: Tung Nguyen (tongueroo@gmail.com)
  License: MIT
```

{% include back_to/dsl-basics.md %}


