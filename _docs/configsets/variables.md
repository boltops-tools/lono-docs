---
title: Configset Variables
nav_text: Variables
categories: configsets
order: 7
---

You can define variables to be made available in your configset code.

## Configset Default Variables

Normally, configsets set default variables in their `vars.rb` file.  Example:

app/configsets/httpd/vars.rb

```ruby
@html =<<-EOL
<h1>configset predefined variables</h1>
<p>Hello from app/configsets/httpd/vars.rb</p>
EOL
```

## User Custom Configset Variables

You can set custom variables with the `config/blueprints/BLUEPRINT/configsets/CONFIGSET.rb`. Notice how the configset variables are scoped to both blueprint and configset. Example:

config/blueprints/ec2/configsets/vars/httpd.rb

```ruby
@html =<<-EOL
<h1>project variables.rb override</h1>
<p>Hello there from config/blueprints/ec2/configsets/vars/httpd.rb</p>
EOL
```

## DSL Variables Access

The DSL Configset is just Ruby so you access the variables directly as instance variables.

```ruby
package("yum",
  httpd: []
)
file("/var/www/html/index.html",
  content: @html
)
service("sysvinit",
  httpd: {
    enabled: true,
    ensureRunning: true,
  }
)
```

The variable here is `@html`.

## ERB Variables Access

For ERB Configsets, you access the variables with ERB.  The `configset.yml` is processed as ERB before being loaded into the CloudFormation template.  This allows you to use ERB to refer to variables:

Example:

```yaml
AWS::CloudFormation::Init:
  config:
    packages:
      yum:
        httpd: []
    files:
      "/var/www/html/index.html":
        content: |
<%= indent(@html, 10) %>
    services:
      sysvinit:
       httpd:
        enabled: 'true'
        ensureRunning: 'true'
```

Note, we're also using the `indent` method to align the YAML content.

## Configsets are Ruby

The configs file is just Ruby actually. So you have the full power of Ruby to organize things however you wish. Example:

config/blueprints/ec2/configsets/vars/httpd.rb

```ruby
@html = IO.read(File.expand_path("html/index.html", __dir__))
```

config/blueprints/ec2/configsets/httpd/html/index.html:

```html
<h2>My html page</h2>
<p>Hello from config/blueprints/ec2/configsets/httpd/html/index.html</p>
```
