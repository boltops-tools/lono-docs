---
title: FindInMap
categories: intrinsic-function
desc: The intrinsic function `Fn::FindInMap` returns the value corresponding to keys in a two-level map that's declared in the Mappings section.
aws_text: Fn::FindInMap
aws_link: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-findinmap.html
---

{{ page.desc }}

The `find_in_map` method is the CloudFormation [{{ page.aws_text }}]({{ page.aws_link }}) equivalent.

## Example Snippet

```ruby
mapping("AmiMap",
  "us-east-1": { Ami: "ami-0de53d8956e8dcf80" },
  "us-west-2": { Ami: "ami-061392db613a6357b" }
)

resource("Instance", "AWS::EC2::Instance",
  InstanceType: ref("InstanceType"),
  ImageId: find_in_map("AmiMap", ref("AWS::Region"), "Ami"),
)
```

## Example Output

```yaml
Mappings:
  AmiMap:
    us-east-1:
      Ami: ami-0de53d8956e8dcf80
    us-west-2:
      Ami: ami-061392db613a6357b
Resources:
  Instance:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType:
        Ref: InstanceType
      ImageId:
        Fn::FindInMap:
        - AmiMap
        - Ref: AWS::Region
        - Ami
```

## mapping method

The `find_in_map` method is used in conjuction with the [mapping]({% link _docs/dsl/basics/mapping.md %}) method.

{% include back_to/intrinsic_functions.md %}


