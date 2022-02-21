---
title: Deploy Infrastructure
---

Let's go ahead and deploy the infrastructure

    lono up demo

The `lono up` command will build the files and then essentially run `aws cloudformation create-stack`.

    $ lono up demo
    Deploy demo-dev stack...
    Creating lono stack for s3 bucket to store templates
    Waiting for stack to complete
    04:02:03AM CREATE_IN_PROGRESS AWS::CloudFormation::Stack lono User Initiated
    04:02:07AM CREATE_IN_PROGRESS AWS::S3::Bucket Bucket
    04:02:08AM CREATE_IN_PROGRESS AWS::S3::Bucket Bucket Resource creation Initiated
    04:02:30AM CREATE_COMPLETE AWS::S3::Bucket Bucket
    04:02:31AM CREATE_COMPLETE AWS::CloudFormation::Stack lono
    Stack success status: CREATE_COMPLETE
    Time took: 30s.
    Building template
        output/demo/template.yml
    Building parameters
        output/demo/params.json

    Will create
      1 AWS::S3::Bucket
      1 Total

    Going to create stack demo-dev with blueprint demo. (y/N)

Type `y` and press enter and you'll see the deployment continue.

    Going to create stack demo-dev with blueprint demo. (y/N) y
    Waiting for stack to complete
    04:03:00AM CREATE_IN_PROGRESS AWS::CloudFormation::Stack demo-dev User Initiated
    04:03:04AM CREATE_IN_PROGRESS AWS::S3::Bucket Bucket
    04:03:06AM CREATE_IN_PROGRESS AWS::S3::Bucket Bucket Resource creation Initiated
    04:03:26AM CREATE_COMPLETE AWS::S3::Bucket Bucket
    04:03:28AM CREATE_COMPLETE AWS::CloudFormation::Stack demo-dev
    Stack success status: CREATE_COMPLETE
    Time took: 30s
    Created demo-dev stack.

    Outputs:

    BucketName = demo-dev-bucket-1p4y43txdk9zg
    $

You can see the bucket got created. You could have of bypass the prompt with the `-y` option. IE: `lono up demo -y`.

Note, on the very first run a lono s3 bucket is created to store the CloudFormation templates. This allows us to use much larger CloudFormation template up to 1MB. See [CloudFormation Limits](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cloudformation-limits.html).

Next, we'll make some changes to the infrastructure code.
