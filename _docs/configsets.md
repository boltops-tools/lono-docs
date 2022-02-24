---
title: Configsets
---

Configsets are essentially configuration management embedded into the CloudFormation template. You can use configsets to install and configure software on your EC2 instances automatically. Lono allows you to use configsets in a reusable way.

## Configuration Management Tool

There are several configuration management tools out there: [chef](https://www.chef.io/configuration-management/), [puppet](https://puppet.com/), [ansible](https://www.ansible.com/), [salt](https://docs.saltstack.com/en/latest/), [configsets](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-init.html).  They all can perform these 3 steps:

1. Install a package
2. Configure it
3. Run it as a Service

{% include configsets/example.md %}

## Usage

Your project configsets are located in the `app/configsets`. Example:

* app/configsets/cfn-hup/configset.rb
* app/configsets/httpd/configset.rb

You tell lono to add them to CloudFormation templates with configs. Example:

config/blueprints/ec2/configsets.rb

```ruby
configset("cfn-hup", resource: "Instance")
configset("httpd", resource: "Instance")
```

This installs [cfn-hup](https://github.com/boltopspro/cfn-hup) and [httpd](https://github.com/boltopspro/httpd) on the EC2 instance.

More specifically, lono adds the 2 configsets to the CloudFormation template resource with the logical id `Instance`.  The cfn-hup and httpd configsets are added to the `Instance.Metadata.AWS::CloudFormation::Init` attribute.

You have full control over which configsets to use for each template.

## How They Work

Configsets do not magically get applied after being added to the CloudFormation template though.  The `cfn-init` script must be called to apply the configset. Usually the `cfn-init` script is called in the UserData script. This ensures configsets are applied when instances are launched. Additionally, the [cfn-hup](https://github.com/boltopspro/cfn-hup) script can be set up to apply configsets continuously.

{% include configsets/cfn-init.md %}

Configsets ultimately work with [cfn-init](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-init.html) and [AWS::CloudFormation::Init](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-init.html). The Lono configsets concept empowers you to reuse configsets.


