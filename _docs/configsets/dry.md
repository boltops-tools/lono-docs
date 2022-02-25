---
title: "DRY: Reusable Configusets"
nav_text: DRY
categories: configsets
order: 1
---

Typically, configsets are directly hardcoded into the CloudFormation template. Unfortunately, this makes them hard to reuse. IE: You copy and paste the configset code between CloudFormation templates.

With Lono, configsets are define separately from the template. Lono takes the configsets and dynamically adds them to your CloudFormation templates. This allows them to be reusable with different templates.

## Example

Let's say you have two blueprints: ec2 and asg.

* The ec2 blueprint has an `Instance` resource.
* The asg blueprint has an `LaunchConfiguration` resource.

You can reuse the same configsets for both blueprints by specifying them in the `configsets.rb`. Example:

config/blueprints/ec2/configsets.rb:

```ruby
configset("cfn-hup", resource: "Instance")
configset("httpd", resource: "Instance")
```

config/blueprints/asg/configsets.rb:

```ruby
configset("cfn-hup", resource: "LaunchConfiguration")
configset("httpd", resource: "LaunchConfiguration")
```

Maybe even more importantly, if you make an update or fix a bug in the configset code, it's fixed everywhere. 

## UserData cfn-init

The UserData script for the ec2 blueprint would call `cfn-init` like so:

```bash
#!/bin/bash
/opt/aws/bin/cfn-init -v --stack ${AWS::StackName} --resource Instance --region ${AWS::Region}
```

The asg blueprint's UserData would call `cfn-init` like this:

```bash
#!/bin/bash
/opt/aws/bin/cfn-init -v --stack ${AWS::StackName} --resource LaunchConfiguration --region ${AWS::Region}
```

Notice that the `--resource` option is `Instance` vs `LaunchConfiguration`. This is the CloudFormation resource that the configset is associated with.

The beauty is that you can choose whichever configsets are needed.  You don't have to copy and paste the configset into different templates. Just configure them, and lono adds them into the CloudFormation template for you.
