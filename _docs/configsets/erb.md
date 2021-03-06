---
title: Configset ERB
nav_text: ERB
categories: configsets
order: 5
---

Configsets can be written with YAML.  Writing configsets with YAML can be useful for very simple configsets. Lono adds a little Ruby sprinkles by allowing you to use ERB templating also.

## Example

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
        enabled: true
        ensureRunning: true
```

The `indent` method is a built-in helper for ERB. It aligns the text and is useful for YAML-based configsets.  The `@html` variable can be set by the author of the configset or overridden by you with [variables]({% link _docs/configsets/variables.md %}).
