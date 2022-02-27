---
title: Configsets
---

Configsets are essentially configuration management embedded into the CloudFormation template. You can use configsets to install and configure software on your EC2 instances automatically. Lono allows you to use configsets in a reusable way by dynamically adding them to the template.

## Configuration Management Tool

There are several configuration management tools out there: [chef](https://www.chef.io/configuration-management/), [puppet](https://puppet.com/), [ansible](https://www.ansible.com/), [salt](https://docs.saltstack.com/en/latest/). They all can perform these 3 steps:

1. Install a package
2. Configure it
3. Run it as a Service

[Configsets](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-init.html) is just configuration management software provided by AWS for free. Configsets are very lightweight. Though they, like all other configuration management tools, have their quirks, they can work for companies who don't have the time or budget to use other tools. The [cfn-init](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-init.html) script, which runs and applies configsets, is preinstalled on Amazon Linux.

