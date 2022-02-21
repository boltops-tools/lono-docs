---
title: Split
categories: intrinsic-function
desc: To split a string into a list of string values so that you can select an element from the resulting string list, use the `Fn::Split` intrinsic function. Specify the location of splits with a delimiter, such as , (a comma). After you split a string, use the `Fn::Select` function to pick a specific element.
aws_text: Fn::Split
aws_link: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-split.html
---

{{ page.desc }}

The `split` method is the CloudFormation [{{ page.aws_text }}]({{ page.aws_link }}) equivalent.

## Example Snippet

```ruby
resource("Instance", "AWS::EC2::Instance",
  InstanceType: ref("InstanceType"),
  ImageId: "ami-0de53d8956e8dcf80",
  SecurityGroupIds: split(",", ref("SecurityGroups"))
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
      SecurityGroupIds:
        Fn::Split:
        - ","
        - Ref: SecurityGroups
```

{% include back_to/intrinsic_functions.md %}


