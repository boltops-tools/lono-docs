---
title: Condition
category: dsl-basics
desc: The optional Conditions section contains statements that define the circumstances
  under which entities are created or configured.
aws_text: Conditions
aws_link: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/conditions-section-structure.html
---

{{ page.desc }}

The `condition` method maps to the CloudFormation Template Anatomy [{{ page.aws_text }}]({{ page.aws_link }}) section.

## Example Snippets

There are 2 forms for conditions.  Here are example snippets:

```ruby
# medium form
condition "CreateProdResources", equals(ref("EnvType"), "prod")

# medium form with a Fn::Equals example
condition("CreateDevResources",
  "Fn::Equals": [
    ref("EnvType"),
    "dev"
  ]
)

# long form
condition("CreateStagResources",
  "Fn::Equals": [
    {"Ref": "EnvType"},
    "stag"
  ]
)
```

## Output

```yaml
Conditions:
  CreateProdResources:
    Fn::Equals:
    - Ref: EnvType
    - prod
  CreateDevResources:
    Fn::Equals:
    - Ref: EnvType
    - dev
  CreateStagResources:
    Fn::Equals:
    - Ref: EnvType
    - stag
```

{% include back_to/dsl-basics.md %}


