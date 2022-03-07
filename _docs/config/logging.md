---
title: Config Logging
nav_text: Logging
category: config
order: 2
---

You can customize Lono logger like so

config/app.rb

```ruby
Lono.configure do |config|
  config.logger.level = "info"
end
```

{% include config/reference/header.md %}
{% include config/reference/logging.md %}
{% include config/reference/footer.md %}
