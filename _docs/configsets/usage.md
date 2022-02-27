---
title: Usage
nav_text: Usage
categories: configsets
order: 2
---

{% include configsets/example.md %}

## Usage

You can **define** configsets in the `app/configsets`. Example:

* app/configsets/cfn-hup/configset.rb
* app/configsets/httpd/configset.rb

You **configure** configsets and tell lono to add them to CloudFormation templates with configs, either in `app/blueprints/BLUEPRINT/config/configsets.rb` or `config/blueprints/BLUEPRINT/configsets.rb`. Example:

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


