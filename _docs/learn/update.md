---
title: Update Infrastructure
---

Let's update the infrastructure.

    lono up demo

Lono will show you a preview of the changes and prompt you to update the infrastructure.

    $ lono up demo
    Deploying demo-dev stack
    ...
    Template Changes:
    => diff /tmp/lono/diff/template/existing.yml output/demo/template.yml
    No changes

    Parameter Changes:
    Modified:
        AccessControl: Private -> PublicRead

    Change Set Changes:
    Determining Change Set......
    Resource Changes
        Modify AWS::S3::Bucket: Bucket demo-dev-bucket-1p4y43txdk9zg

    Are you sure you want to update the demo-dev stack? (y/N)

{% include intro/previews.md %}

You are also prompted for confirmation. Type `y` and press enter.

    Are you sure you want to update the demo-dev stack? (y/N) y
    Waiting for stack to complete
    04:05:13AM UPDATE_IN_PROGRESS AWS::CloudFormation::Stack demo-dev User Initiated
    04:05:19AM UPDATE_IN_PROGRESS AWS::S3::Bucket Bucket
    04:05:39AM UPDATE_COMPLETE AWS::S3::Bucket Bucket
    04:05:41AM UPDATE_COMPLETE_CLEANUP_IN_PROGRESS AWS::CloudFormation::Stack demo-dev
    04:05:42AM UPDATE_COMPLETE AWS::CloudFormation::Stack demo-dev
    Stack success status: UPDATE_COMPLETE
    Time took: 30s
    Updated demo-dev stack.

    Outputs:

    BucketName = demo-dev-bucket-1p4y43txdk9zg
    $

The modification has been deployed. You can configure with the AWS CLI. It will look something like this:

    $ aws s3api get-bucket-acl --bucket demo-dev-bucket-1p4y43txdk9zg | jq '.Grants[1]'
    {
      "Grantee": {
        "Type": "Group",
        "URI": "http://acs.amazonaws.com/groups/global/AllUsers"
      },
      "Permission": "READ"
    }
    $

Next, we'll destroy the infrastructure.
