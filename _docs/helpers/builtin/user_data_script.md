---
title: user_data_script Helper
nav_text: User Data
category: builtin-helpers
order: 4
---

The `user_data_script` helper is use to load the UserData scripts. The `user_data_script` reads the file that the `@user_data_script` [variable]({% link _docs/layering/variables.md %}) is set to.

## Example

Let's use an example to explain how it works. Say you have a template with an EC2 instance resource with the UserData property configured:

```ruby
resource("Instance", "AWS::EC2::Instance",
  InstanceType: ref("InstanceType"),
  UserData: base64(sub(user_data_script)),
)
```

In the variables file, set the `@user_data_script` variable to the path of the script.

config/blueprints/demo/vars/dev.rb:

```ruby
@user_data_script = "config/blueprints/demo/user_data/bootstrap.sh"
```

Make sure that the script exists. Example:

config/blueprints/demo/user_data/bootstrap.sh

    #!/bin/bash
    /opt/aws/bin/cfn-init -v --stack ${AWS::StackName} --resource Instance --region ${AWS::Region}
    uptime