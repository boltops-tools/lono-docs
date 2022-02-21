---
title: Sub
categories: intrinsic-function
desc: The intrinsic function `Fn::Sub` substitutes variables in an input string with values that you specify. In your templates, you can use this function to construct commands or outputs that include values that aren't available until you create or update a stack.
aws_text: Fn::Sub
aws_link: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-sub.html
---

{{ page.desc }}

The `sub` method is the CloudFormation [{{ page.aws_text }}]({{ page.aws_link }}) equivalent.

## Example Snippet

```ruby
resource("Instance", "AWS::EC2::Instance",
  InstanceType: ref("InstanceType"),
  ImageId: "ami-0de53d8956e8dcf80",
  UserData: sub("hello ${k1} ${k2}", k1: "v1", k2: "v2")
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
      UserData:
        Fn::Sub:
        - hello ${k1} ${k2}
        - k1: v1
          k2: v2
```

{% include back_to/intrinsic_functions.md %}


