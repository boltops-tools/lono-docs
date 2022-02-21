---
title: Destroy Infrastructure
---

Now that we've seen how to deploy, let's clean up and tear down the resources.

To destroy the resources, run:

    lono down demo

You'll be prompted to make sure you really want to delete these resources.

    $ lono down demo
    Will delete
      1 AWS::S3::Bucket
      1 Total

    Are you sure you want to delete the demo-dev stack? (y/N)

We are prompted for confirmation. Type `y` and press enter to destroy the infrastructure.

    Are you sure you want to delete the demo-dev stack? (y/N) y
    Waiting for stack to complete
    04:06:51AM DELETE_IN_PROGRESS AWS::CloudFormation::Stack demo-dev User Initiated
    Stack demo-dev deleted.
    Time took: 5s
    $

Congrats! You have successfully created, modified, and destroy infrastructure with lono.

Next, we'll look at some next steps.
