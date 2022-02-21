---
title: lono down
reference: true
---

## Usage

    lono down BLUEPRINT

## Description

Delete CloudFormation blueprint

## Examples

    $ lono down demo
    Are you sure you want to delete the demo-dev stack? (y/N)
    y
    Deleted demo-dev stack.
    $

Lono prompts you with an "Are you sure?" message before the stack gets deleted.  If you would like to bypass the prompt, you can use the `-y` flag.

    $ lono down demo -y
    Deleted demo-dev stack.
    $


## Options

```
    [--wait], [--no-wait]  # Wait for stack operation to complete.
                           # Default: true
y, [--yes], [--no-yes]     # Skip are you sure prompt
```

