---
title: Config App
nav_text: App
category: config
order: 1
---

You can customize core lono framework settings with

config/app.rb

```ruby
Lono.configure do |config|
  config.logger.level = "info"
end
```

For all the options, see [Config Reference Docs]({% link _docs/config/reference.md %}).