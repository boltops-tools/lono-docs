---
title: Transform
category: dsl-basics
desc: The optional Transform section specifies one or more macros that AWS CloudFormation
  uses to process your template.
aws_text: Transform
aws_link: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/transform-section-structure.html
---

{{ page.desc }}

The `transform` method maps to the CloudFormation Template Anatomy [{{ page.aws_text }}]({{ page.aws_link }}) section.

## Example Snippet 1

```ruby
transform("MyMacro", "Aws::Serverless")
```

## Outputs

```yaml
Transform:
- MyMacro
- Aws::Serverless
```

## Example Snippet 2

```ruby
transform("MyMacro")
```

## Outputs

```yaml
Transform: MyMacro
```

{% include back_to/dsl-basics.md %}


