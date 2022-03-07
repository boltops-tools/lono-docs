---
title: lono build
reference: true
---

## Usage

    lono build BLUEPRINT

## Description

Build template

Generates CloudFormation template, parameter files, and scripts in lono project and writes them to the `output` folder.

## Examples

    lono build BLUEPRINT
    lono build BLUEPRINT --clean
    lono g BLUEPRINT --clean # shortcut

## Example Output

    $ lono build ec2
    Building template, parameters, and scripts
    Building template:
      output/templates/ec2.yml
    Building parameters:
      output/params/ec2.json
    $


## Options

```
[--quiet], [--no-quiet]  # silence the output
[--clean], [--no-clean]  # remove all output files before generating
                         # Default: true
```

