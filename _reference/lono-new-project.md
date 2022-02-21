---
title: lono new project
reference: true
---

## Usage

    lono new project NAME

## Description

Generates new project.

## Example

    $ lono new project infra
    => Creating new project called infra.
          create  infra
          create  infra/.gitignore
          create  infra/Gemfile
          create  infra/README.md
          create  infra/config/app.rb
    => Initialize git repo
             run  git init from "."
    Initialized empty Git repository in /home/ec2-user/environment/infra/.git/
    => Installing dependencies with: bundle install
    Resolving dependencies...Fetching gem metadata from https://rubygems.org/.......
    ............................
    Using concurrent-ruby 1.1.9
    ...
    Bundle complete! 1 Gemfile dependency, 40 gems now installed.
    Use `bundle info [gemname]` to see where a bundled gem is installed.
    ================================================================
    Congrats 🎉 You have successfully created a lono project.

        cd infra

    To generate a new blueprint:

        lono new blueprint demo --examples

    To deploy:

        lono up demo

    More info: https://lono.cloud/
    $


## Options

```
[--bundle], [--no-bundle]      # Runs bundle install on the project
                               # Default: true
[--examples], [--no-examples]  # Also generate blueprint example
[--force]                      # Bypass overwrite are you sure prompt for existing files
[--git], [--no-git]            # Git initialize the project
                               # Default: true
[--quiet], [--no-quiet]        # Quiet output.
```

