---
title: Base64
categories: intrinsic-function
desc: The intrinsic function `Fn::Base64` returns the Base64 representation of the input string. This function is typically used to pass encoded data to Amazon EC2 instances by way of the UserData property.
aws_text: Fn::Base64
aws_link: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-base64.html
---

{{ page.desc }}

The `base64` method is the CloudFormation [{{ page.aws_text }}]({{ page.aws_link }}) equivalent.

## Example Snippet

```ruby
resource("Instance", "AWS::EC2::Instance",
  InstanceType: "t3.micro",
  ImageId: "ami-0de53d8956e8dcf80",
  UserData: base64("#!/bin/bash\necho hi")
)
```

## Example Output

```yaml
Resources:
  Instance:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType: t3.micro
      ImageId: ami-0de53d8956e8dcf80
      UserData:
        Fn::Base64: |-
          #!/bin/bash
          echo hi
```

{% include back_to/intrinsic_functions.md %}


