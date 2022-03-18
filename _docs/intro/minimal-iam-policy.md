---
title: Minimal IAM Policy
nav_text: Minimal IAM
categories: intro
order: 6
---

The IAM user you use to run the [lono up](/reference/lono-cfn-deploy/) command needs a minimal set of IAM policies in order to deploy. Here is a table of the baseline services needed:

Service | Description
--- | ---
CloudFormation | To create the CloudFormation stacks that then creates the the AWS resources that your creates.
S3 | To create the lono managed s3 bucket. Lono uploads the generated CloudFormation template here. [App Files]({% link _docs/more/lono-files.md %}) are also uploaded here.

However, it really depends on what your CloudFormation templates provision. If your templates provision an ec2 instance like the demo blueprint then you'd need EC2 also.

## Instructions

It is recommended that you create an IAM group and associate it with the IAM users that need access to use [lono up](/reference/lono-cfn-deploy/).  Here are starter instructions and a policy that you can tailor for your needs:

## IAM Commands: All Bucket Permissions

Here's a summary of the commands:

    aws iam create-group --group-name Lono
    cat << 'EOF' > /tmp/lono-iam-policy.json
    {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Effect": "Allow",
                "Action": [
                    "cloudformation:*",
                    "s3:*"
                 ],
                "Resource": [
                    "*"
                ]
            }
        ]
    }
    EOF
    aws iam put-group-policy --group-name Lono --policy-name LonoPolicy --policy-document file:///tmp/lono-iam-policy.json

Finally, create a user and add the user to IAM group. Here's an example:

    aws iam create-user --user-name tung
    aws iam add-user-to-group --user-name tung --group-name Lono

## IAM Commands: Limited Bucket Permissions

If you wish to have a more limited s3 policy, here's one way to restrict it.

Create AWs AM

    aws iam create-group --group-name Lono
    cat << 'EOF' > /tmp/lono-iam-policy.json
    {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Sid": "sid0",
                "Effect": "Allow",
                "Action": "s3:*",
                "Resource": [
                    "arn:aws:s3:::lono-bucket-*",
                    "arn:aws:s3:::-*bucket-*"
                ]
            },
            {
                "Sid": "sid1",
                "Effect": "Allow",
                "Action": [
                    "cloudformation:*",
                 ],
                "Resource": [
                    "*"
                ]
            }
        ]
    }
    EOF
    aws iam put-group-policy --group-name Lono --policy-name LonoPolicy --policy-document file:///tmp/lono-iam-policy.json

Add user to group

    aws iam add-user-to-group --group-name Lono --user-name tung

Note, the policy allows `*-bucket-*` and is somewhat redundant to allow the Getting Started Guide to work.
