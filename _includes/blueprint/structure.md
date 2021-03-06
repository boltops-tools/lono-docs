## Basic Structure

The most basic blueprint structure simply has one file.

    app/blueprints/demo
    └── template.rb

The `template.rb` is what you'll work with mostly.

Hopefully, that gives you a basic idea of a lono blueprint structure.

{% if include.full %}

## Full Structure

Here's the full Lono blueprint structure.

    app/blueprints/demo
    ├── config
    ├── helpers
    │   └── custom_helper.rb
    ├── seed
    │   └── vars
    │       ├── dev.rb
    │       └── prod.rb
    └── template.rb

All of the folders and files are optional. Just add them when needed.

## Files and Folders

File / Folders  | Description
------------- | -------------
config | Pre-defined config params and vars that ship with the blueprint. They can be overriden by user customizations in `config/blueprints/BLUEPRINT/{params,vars}`. See: [Layering Basics]({% link _docs/layering/basics.md %}).
helpers | Define your custom helpers here. The custom helpers are available to templates, vars, and params. This is how you extend the Lono framwork as a first-class citizen. The helpers are scoped only to the specific blueprint and won't interfere with other blueprints. Helpers are covered in detail in [custom helpers]({% link _docs/helpers.md %}).
seed/vars | You can define files that the [lono seed]({% link _docs/config/seed.md %}) will use to generate starter vars files.
template.rb | Where CloudFormation templates are defined.  Refer to the [DSL docs]({% link _docs/dsl.md %}) for the syntax. You can also define resources in within the `template` folder. Any file with the `.rb` extension within this folder is evaluated by the [DSL]({% link _docs/dsl.md %}).

{% endif %}
