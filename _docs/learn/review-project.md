---
title: Review Project
---

Let's explore the generated app folder.

## Demo Blueprint

Let's check out the generated code.

app/blueprints/demo/template.rb

```ruby
parameter("BucketName", Conditional: true)
parameter("AccessControl", Default: "Private")

resource("Bucket", "AWS::S3::Bucket",
  BucketName: ref("BucketName", Conditional: true),
  AccessControl: ref("AccessControl"),
)

output("BucketName", ref("Bucket"))
```

You can see that the starter demo blueprint is written in a DSL.  This demo blueprint creates a s3 bucket.

The Lono DSL closely resembles the [CloudFormation Template anatomy sections](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-anatomy.html). The DSL methods pretty much map one-to-one. Docs: [Lono DSL Basics]({% link _docs/dsl/basics.md %})

Lono Method | CloudFormation Section
---|---
[parameter]({% link _docs/dsl/basics/parameter.md %}) | [Parameters](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/parameters-section-structure.html)
[resource]({% link _docs/dsl/basics/resource.md %}) | [Resources](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/resources-section-structure.html)
[output]({% link _docs/dsl/basics/output.md %}) | [Outputs](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/outputs-section-structure.html)

One thing that may stand out is the `Conditional` option. This is a CloudFormation pattern that is common enough that lono has encapsulated it: [Conditional Parameter](). In short, it just uses `AWS::NoValue` as the value when the parameter is a blank string, `BucketName` in this case.

Next, we'll build the CloudFormation template.
