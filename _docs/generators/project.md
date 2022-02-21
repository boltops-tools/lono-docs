---
title: Project Generator
nav_text: Project
category: generators
order: 1
---

The project generator creates a starter Lono project structure.

## Blank Project


    $ lono new project infra
    => Creating new project called infra.
          create  infra
          create  infra/.gitignore
          create  infra/Gemfile
          create  infra/README.md
          create  infra/config/app.rb
    ================================================================
    Congrats 🎉 You have successfully created a lono project.

        cd infra

    To generate a new blueprint:

        lono new blueprint demo --examples

    To deploy:

        lono up demo

    More info: https://lono.cloud/
    $

## Project with Examples

You can also tell the project generator to generate a project with some starter examples.

    $ lono new project infra --examples
    => Creating new project called infra.
          create  infra
          create  infra/.gitignore
          create  infra/Gemfile
          create  infra/README.md
          create  infra/config/app.rb
    => Creating new blueprint called demo.
          create  infra/app/blueprints/demo
          create  infra/app/blueprints/demo/template.rb
    ================================================================
    Congrats 🎉 You have successfully created a lono project.

        cd infra

    To deploy:

        lono up demo

    More info: https://lono.cloud/
    $