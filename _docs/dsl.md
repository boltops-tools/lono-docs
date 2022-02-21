---
title: DSL
---

With Lono, you write your CloudFormation template with a DSL. The DSL is actually just Ruby code. This means we get the full power of a programming language. We can use loops, define methods, modules, etc. At the same time, the Lono DSL stays very close to the [declarative nature of CloudFormation](https://blog.boltops.com/2018/02/14/aws-cloudformation-declarative-infrastructure-code-tutorial). We get the best of both worlds.

Here's an example of what the DSL looks like.

{% include dsl/example.md %}
