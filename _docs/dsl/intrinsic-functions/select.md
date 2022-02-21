---
title: Select
categories: intrinsic-function
desc: The intrinsic function `Fn::Select` returns a single object from a list of objects by index.
aws_text: Fn::Select
aws_link: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-select.html
---

{{ page.desc }}

The `select` method is the CloudFormation [{{ page.aws_text }}]({{ page.aws_link }}) equivalent.

## Example Snippet

```ruby
resource("Subnet0", "AWS::EC2::Subnet",
  VpcId: ref("Vpc"),
  CidrBlock: select("0", ref("DbSubnetIpBlocks"))
)
```

## Example Output

```yaml
Resources:
  Subnet0:
    Type: AWS::EC2::Subnet
    Properties:
      VpcId:
        Ref: Vpc
      CidrBlock:
        Fn::Select:
        - '0'
        - Ref: DbSubnetIpBlocks
```

{% include back_to/intrinsic_functions.md %}


