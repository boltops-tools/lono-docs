---
title: Notification ARNs
categories: more
order: 5
---

You can specific notification arns for CloudFormation stack related events with a CLI option or in [config/app.rb]({% link _docs/config/app.md %}). Example:

config/envs/prod.rb

```ruby
Lono.configure do |config|
  config.notification_arns = ["arn:aws:sns:us-west-2:112233445566:my-sns-topic1"]
end
```

This sets the `notification_arns` option to all `lono up` so you don't have to remember typing it.
