---
title: Configsets Layering Debugging
nav_text: Debugging
categories: configsets-layering
order: 1
---

## Debugging Configset Layering

You can debug layers by turning on logging to debug to see them.

config/app.rb

```ruby
Lono.configure do |config|
  config.logger.level = "debug"
end
```

This will show the **found** layers.

    $ lono build ec2
    Layers for configset httpd:
        app/configsets/httpd/vars.rb
        config/blueprints/ec2/configsets/vars/httpd.rb

## All Considered Layers

If you want to also see all the considered layers use `LONO_SHOW_ALL_LAYERS=1`. Remember, `config.logger.level = "debug"` needs to also be configured.

    $ export LONO_SHOW_ALL_LAYERS=1
    $ lono build ec2
    Layers for configset httpd:
        app/configsets/httpd/vars.rb
        config/configsets/httpd/vars.rb
        app/blueprints/ec2/config/configsets/vars/httpd.rb
        config/blueprints/ec2/configsets/vars/httpd.rb

Note: This will turn on debugging for params and vars layering also. See: [Layering Debugging]({% link _docs/layering/debugging.md %}).