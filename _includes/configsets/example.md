## Configset Example

The configset can be written in [YAML form]({% link _docs/configsets/erb.md %}). This form is what you'll typically see in CloudFormation templates out there. Lono adds a little Ruby sprinkles by allowing you to use ERB templating also. 

app/configsets/httpd/configset.yml

```yaml
AWS::CloudFormation::Init:
  config:
    packages:
      yum:
        httpd: []
    files:
      "/var/www/html/index.html":
        content: <%= @html %>
    services:
      sysvinit:
        httpd:
          enabled: true
          ensureRunning: true
```

This configset will install, configure, and ensure that the httpd server is running, even if the server is rebooted.

The configset can also be written in [DSL form]({% link _docs/configsets/dsl.md %}). This DSL is provided by Lono. The DSL compiles down to YAML and does the same this as the YAML form above. 

app/configsets/httpd/configset.rb

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

The DSL methods are pretty much a one-to-one mapping to the YAML configset fields. 
