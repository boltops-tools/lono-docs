---
title: New Project
---

We'll use [lono new project]({% link _reference/lono-new-project.md %}) to generate a new lono project.

    lono new project infra --examples

For this tutorial, we're using the `--examples` option to generate a starter example.

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
    $

Cd into the folder and check out the files.

    cd infra

For more information about the folders see [Project Structure]({% link _docs/intro/project-structure.md %}).

Next, we'll review generated app folder files.
