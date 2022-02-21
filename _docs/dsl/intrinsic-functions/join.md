---
title: Join
categories: intrinsic-function
desc: The intrinsic function `Fn::Join` appends a set of values into a single value, separated by the specified delimiter. If a delimiter is the empty string, the set of values are concatenated with no delimiter.
aws_text: Fn::Join
aws_link: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-join.html
---

{{ page.desc }}

The `join` method is the CloudFormation [{{ page.aws_text }}]({{ page.aws_link }}) equivalent.

## Example Snippet

```ruby
resource("Instance", "AWS::EC2::Instance",
  InstanceType: ref("InstanceType"),
  ImageId: "ami-0de53d8956e8dcf80",
  Tags: tags(Name: join("-", ref("Param1"), ref("Param2")))
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
      Tags:
      - Key: Name
        Value:
          Fn::Join:
          - "-"
          - - Ref: Param1
            - Ref: Param2
```

{% include back_to/intrinsic_functions.md %}


