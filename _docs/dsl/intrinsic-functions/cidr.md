---
title: Cidr
categories: intrinsic-function
desc: The intrinsic function `Fn::Cidr` returns an array of CIDR address blocks. The number of CIDR blocks returned is dependent on the count parameter.
aws_text: Fn::Cidr
aws_link: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-cidr.html
---

{{ page.desc }}

The `cidr` method is the CloudFormation [{{ page.aws_text }}]({{ page.aws_link }}) equivalent.

## Example Snippet

```ruby
resource("ExampleSubnet", "AWS::EC2::Subnet",
  AssignIpv6AddressOnCreation: "true",
  CidrBlock: select("0", cidr(get_att("ExampleVpc.CidrBlock"), "1", "8")),
  VpcId: ref("ExampleVpc")}
)
```

## Example Output

```yaml
Resources:
  ExampleSubnet:
    Type: AWS::EC2::Subnet
    Properties:
      AssignIpv6AddressOnCreation: 'true'
      CidrBlock:
        Fn::Select:
        - '0'
        - Fn::Cidr:
          - Fn::GetAtt:
            - ExampleVpc
            - CidrBlock
          - '1'
          - '8'
      VpcId:
        Ref: ExampleVpc
```

{% include back_to/intrinsic_functions.md %}


