---
title: Build the Template
---

Let's build the blueprint.

    lono build demo

The `lono build` command builds the blueprint and compiles down the template to the `output` folder.

    $ lono build demo
    Building CloudFormation template for blueprint demo:
        output/demo/template.yml
    Building parameters for blueprint demo:
        output/demo/params.json
    $

## View Files

You can see that the DSL was compiled down to a CloudFormation YAML template.

output/demo/template.yml

```yaml
---
Parameters:
  BucketName:
    Default: ''
    Type: String
  AccessControl:
    Default: Private
    Type: String
Conditions:
  HasBucketName:
    Fn::Not:
    - Fn::Equals:
      - Ref: BucketName
      - ''
Resources:
  Bucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName:
        Fn::If:
        - HasBucketName
        - Ref: BucketName
        - Ref: AWS::NoValue
      AccessControl:
        Ref: AccessControl
Outputs:
  BucketName:
    Value:
      Ref: Bucket
```

Custom parameters values was also compiled down to a JSON file. In this case it's currently empty.

output/demo/params.json

```json
[]
```

This files are useful for debugging. They can actually be used with the `aws cloudformation` CLI commands. Example:

    cd output/demo
    aws cloudformation create-stack --stack-name demo-dev --template-body file://template.yml --parameters file://params.json

Lono makes it easier though by automating the process with the `lono up` command, which we'll cover next.

Next, we'll deploy the infrastructure.
