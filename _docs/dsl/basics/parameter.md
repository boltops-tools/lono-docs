---
title: Parameter
category: dsl-basics
desc: Use the optional Parameters section to customize your templates. Parameters
  enable you to input custom values to your template each time you create or update
  a stack.
aws_text: Parameters
aws_link: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/parameters-section-structure.html
---

{{ page.desc }}

The `parameter` method maps to the CloudFormation Template Anatomy [{{ page.aws_text }}]({{ page.aws_link }}) section.

## Example Snippets

There are 3 forms for conditions.  Here are example snippets:

```ruby
# short form
parameter("AmiId")            # no default, so this is a required parameter
parameter("ImageId", "ami-123") # default is ami-123

# medium form
parameter("Company", Default: "boltops", Description: "instance type")

# long form
parameter("InstanceType" => {
  Default: "t2.micro" ,
  Description: "instance type" ,
})
```

## Example Outputs

```yaml
Parameters:
  AmiId:
    Type: String
  ImageId:
    Default: ami-123
    Type: String
  Company:
    Default: boltops
    Description: instance type
    Type: String
  InstanceType:
    Default: t2.micro
    Description: instance type
    Type: String
```

{% include back_to/dsl-basics.md %}


