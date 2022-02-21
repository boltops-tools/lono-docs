---
title: GetAZs
categories: intrinsic-function
desc: The intrinsic function `Fn::GetAZs` returns an array that lists Availability Zones for a specified region in alphabetical order. Because customers have access to different Availability Zones, the intrinsic function `Fn::GetAZs` enables template authors to write templates that adapt to the calling user's access. That way you don't have to hard-code a full list of Availability Zones for a specified region.
aws_text: Fn::GetAZs
aws_link: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-getavailabilityzones.html
---

{{ page.desc }}

The `get_azs` method is the CloudFormation [{{ page.aws_text }}]({{ page.aws_link }}) equivalent.

## Example Snippet

```ruby
resource("MySubnet", "AWS::EC2::Subnet",
  VpcId: ref("Vpc"),
  CidrBlock: "10.0.0.0/24",
  AvailabilityZone: select("0", get_azs(''))
)
```

## Example Output

```yaml
Resources:
  MySubnet:
    Type: AWS::EC2::Subnet
    Properties:
      VpcId:
        Ref: Vpc
      CidrBlock: 10.0.0.0/24
      AvailabilityZone:
        Fn::Select:
        - '0'
        - Fn::GetAZs: ''
```

{% include back_to/intrinsic_functions.md %}


