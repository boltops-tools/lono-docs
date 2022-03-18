---
title: Version 8 Upgrading Guide
nav_text: Version 8
categories: upgrading
order: 1
---

In Lono v8, significant structural and backward-incompatible changes had to be made to improve the framework. There's no easy answer here. Upgrading requires a brute-force approach. You will likely have to replace CloudFormation stacks entirely.

1. Build a new Lono project
2. Map the blueprint structure over.
3. Deploy each blueprint.
4. Destroy the old stack.

Even though, it may be possible to use the same stack name by customizing it with [Config Names]({% link _docs/config/names.md %}), it's generally not recommended. It's probably better to go forward with a "lift and shift" approach.
