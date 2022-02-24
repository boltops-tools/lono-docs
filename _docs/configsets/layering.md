---
title: Configsets Layering
nav_text: Layering
categories: configsets
order: 8
---

Configsets also support their own notion of variables layering. Remember, variables change how the configset code gets compiled.

## Layering Basics

Most users will usually should just stick to the basic layering levels. Example:

Name | Example | Description
---|---|---
Source Defaults | app/configsets/httpd/vars.rb | Here's where the author defines the configset generic defaults. This lives with the configset source code itself.
User Overrides | config/blueprints/demo/configsets/vars/httpd.rb | How uses can override the configset defaults. Notice how it's scoped to both blueprint and configset. You have fine grain control over it.

The main layer you'll likely want to use is "User Overrides". The general form is:

    config/blueprints/BLUEPRINT/configsets/vars/CONFIGSET.rb

## Full Layering


Name | Example | Description
---|---|---
Source Defaults | app/configsets/httpd/vars.rb | Configset source defaults.
Source Overrides | config/configsets/httpd/vars.rb | Override at the project-level the configset defaults. Since only the configset is specified, these overrides will apply to all blueprints configured to use the configset.
Blueprint Overrides | app/blueprints/demo/config/configsets/vars/httpd.rb | Override at the blueprint-level within the blueprint source code. This allows blueprints to ship their own defaults.
User Overrides | config/blueprints/demo/configsets/vars/httpd.rb | Override at the user project-level. This allows user customizations.

Notes:

* "Source" layers only specify the configset, which means that their values will apply to all blueprints.
* Other layers scope both the configset and blueprint. These variables are more targetted.
