---
title: Multiple vs Single Accounts
nav_text: Multiple Accounts
categories: more
order: 4
---

There are 2 strategies for deploying your environments on AWS that are worth discussing.

1. Multiple AWS Accounts
2. Single AWS Account

## Mutiple AWS Accounts

In multiple-account approach, each environment is deployed to a separate AWS account. For example prod, management, and dev are all on completely separate AWS accounts.

The multiple-account strategy is commonly used today because of the benefits.  You get complete isolation between the environments. You have nice guardrail against accidentally doing something on prod that was meant for dev.

Additionally, AWS supports many features that make using multiple-account much easier today.  [AWS Organizations](https://aws.amazon.com/organizations/) help you centrally create, manage, and organize multiple AWS accounts from a parent master account.  Also, the aws cli and AWS sdk support switching AWS accounts with [Named Profiles](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-profiles.html) and the `AWS_PROFILE` env var.  The AWS Console brower experience also supports switching between accounts easily.

The main drawbrack with the multiple-account is that you have to remember to switch accounts.

Overall, the multiple-account approach is the recommended approach.

## Single AWS Account

In a single-account approach, each environment like prod and dev is deployed to the same AWS account.

The benefit is that you don't have to remember to switch `AWS_PROFILE`.

The drawbracks is less isolation between the environments. You must be more careful to achieve isolation with AWS features like IAM policies, security groups, etc.

## Thoughts

Generally, the multiple-account approach is the recommended approach sense it provides such a huge security benefit.
