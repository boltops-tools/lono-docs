---
title: Pros and Cons
nav_text: Pros and Cons
categories: configsets
order: 9
---

You might be wondering whether or not to use configsets vs other tools like vs chef vs puppet vs ansible vs salt. This page can help.

## Configset Pros

* Very lightweight. There's not much to learn. The docs are literally 2 pages: [AWS::CloudFormation::Init](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-init.html) and [cfn-init](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-init.html).
* The syntax is simple. It's just YAML.
* It can pretty much do all the basic things other configuration management tools do. 1. Install Package 2. Configure It 3. Run it as Service
* It's preinstalled on Amazon Linux. That's one less setup step.
* It's free.

## Configset Cons

* Very lightweight. It's not as feature-full or rich as other configuration management tools.
* The syntax is simple. YAML doesn't allow for more powerful programming constructs. The Lono [Configset DSL]({% link _docs/configsets/dsl.md %}) addresses this.
* They're hard to reuse. They're typically hardcoded into CloudFormation templates.  Lono addresses this with its ability to add configsets to the template dynamically. See: [DRY Docs]({% link _docs/configsets/dry.md %})
* There's no dashboard or enterprise version that provides a visualization of the servers using configsets.
* It's AWS-specific. You'll have to rewrite or use another configuration management tool for other clouds or on-prem. You can probably install cfn-init and get it to work on other OSes or clouds, but AWS wrote it for Amazon Linux.
* It's tightly coupled to the CloudFormation template lifecycle. You literally have to update the stack template to reapply the configset. Though the script can be called directly and passed in a file, it would take time to figure out.
* It's lesser well known. This page can help: [Debugging Configsets]({% link _docs/configsets/debugging.md %})

## Question: Should you use configsets?

As usual, it depends.

There are some no-brainers, though. If your company does not use CloudFormation, then it really doesn't make sense to use configsets.

If your company uses CloudFormation and it doesn't have the time to invest in a full-fledged configuration management tool, then it can make perfect sense to use. See all the pros listed above. Though configsets can be quirky and are definitely not without wrinkles, Lono makes them easier to use. Importantly, Lono makes it possible to reuse configsets.
