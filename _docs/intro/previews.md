---
title: Previews
nav_text: Previews
categories: intro
order: 4
---

Lono runs a "plan" that provides a preview of what will be deployed by showing the differences.

{% include intro/previews.md %}

## Example

    $ lono up demo
    Deploying demo-dev stack
    ...
    Template Diff:
    => diff /tmp/lono/diff/template/existing.yml output/demo/template.yml
        4 insertions(+), 9 deletions(-)

    Parameter Diff:
    Added:
        Parameter1: Value1
    Removed:
        Parameter2: Value2
    Modified:
        GroupDescription: desc 1 -> desc 2

    Change Set Diff:
    Determining Change Set.......
        Modify AWS::EC2::SecurityGroup: SecurityGroup demo-dev-SecurityGroup-10RCAAYLFSKT6
    Changes to outputs
    Added:
        SecurityGroup
    ...
    Updated demo-dev stack.
