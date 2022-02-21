---
title: ImportValue
categories: intrinsic-function
desc: The intrinsic function `Fn::ImportValue` returns the value of an output exported by another stack. You typically use this function to create cross-stack references. In the following example template snippets, Stack A exports VPC security group values and Stack B imports them.
aws_text: Fn::ImportValue
aws_link: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-importvalue.html
---

{{ page.desc }}

The `import_value` method is the CloudFormation [{{ page.aws_text }}]({{ page.aws_link }}) equivalent.

## Example Snippet

```ruby
resource("Instance", "AWS::EC2::Instance",
  InstanceType: ref("InstanceType"),
  ImageId: "ami-0de53d8956e8dcf80",
  NetworkInterfaces: {
    GroupSet: [import_value(sub("${NetworkStack}-SecurityGroupID"))],
    AssociatePublicIpAddress: "true",
    DeviceIndex: "0",
    DeleteOnTermination: "true",
    SubnetId: import_value(sub("${NetworkStack}-SubnetID"))
  }
)
```

## Example Output

```yaml
Resources:
  Instance:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType:
        Ref: InstanceType
      ImageId: ami-0de53d8956e8dcf80
      NetworkInterfaces:
        GroupSet:
        - Fn::ImportValue:
            Fn::Sub:
            - "${NetworkStack}-SecurityGroupID"
            - {}
        AssociatePublicIpAddress: 'true'
        DeviceIndex: '0'
        DeleteOnTermination: 'true'
        SubnetId:
          Fn::ImportValue:
            Fn::Sub:
            - "${NetworkStack}-SubnetID"
            - {}
```

{% include back_to/intrinsic_functions.md %}


