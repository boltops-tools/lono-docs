---
title: Ref
categories: intrinsic-function
desc: The intrinsic function `Ref` returns the value of the specified parameter or resource.
aws_text: Ref
aws_link: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-ref.html
---

{{ page.desc }}

The `ref` method is the CloudFormation [{{ page.aws_text }}]({{ page.aws_link }}) equivalent.

## Example Snippet

```ruby
resource("MyEip", "AWS::EC2::EIP",
  InstanceId: ref("MyEc2Instance")
)
```

## Example Output

```yaml
Resources:
  MyEip:
    Type: AWS::EC2::EIP
    Properties:
      InstanceId:
        Ref: MyEc2Instance
```

{% include back_to/intrinsic_functions.md %}


