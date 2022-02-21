---
title: Project Structure
nav_text: Project Structure
category: intro
order: 3
---

Here's an example project structure.

    project
    ├── app
    │   └── blueprints
    │       └── demo
    │           └── template.rb
    ├── config
    │   ├── app.rb
    │   └── blueprints
    │       └── demo
    │           ├── params
    │           │   ├── dev.txt
    │           │   └── prod.txt
    │           └── vars
    │               ├── dev.rb
    │               └── prod.rb
    └── output
        └── demo
            ├── params.json
            └── template.yml

## Files and Folders

To explain the files and folders, we'll use the `demo` blueprint as an example:

File / Folders  | Description
------------- | -------------
app/blueprints | Where blueprints live. [Blueprints]({% link _docs/blueprints.md %}) contain code to build CloudFormation templates. They can be configured with parameters and variables in `config/blueprints`. [Blueprint Structure Docs]({% link _docs/blueprints/structure.md %}).
app/blueprints/demo/template.rb | Example of a blueprint `template.rb`. This is where you define your source code with the [Lono DSL]({% link _docs/dsl.md %}).
app/configsets | Where configsets live. [Configsets]({% link _docs/configsets.md %}) are essentially configuration management. Lono can inject them into your template making them reusable. They can be configured with `config/blueprints/BLUEPRINT/configsets`.
config/app.rb | Lono's behavior can be tailored with [config/app.rb]({% link _docs/config.md %}).
config/blueprints/demo/configsets | Where configsets are configured.  You can selectively add configsets to templates. [Configsets Docs]({% link _docs/configsets.md %})
config/blueprints/demo/params | Where CloudFormation run-time parameters can be defined.  [Parameters]({% link _docs/config/params.md %}) are defined with env-like files.
config/blueprints/demo/vars | Where Lono variables can be defined.  [Variables]({% link _docs/config/variables.md %}) can be used to compile down different templates. This is useful when run-time parameters do not suffice.
output/demo/params | Where the generated CloudFormation parameters files get written to.
output/demo/templates | Where the generated CloudFormation templates get written to.

That's the basic lono project structure.
