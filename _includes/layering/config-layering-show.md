To see the layers being used, use the `config.layering.show` option.

config/app.rb

```ruby
Lono.configure do |config|
  config.layering.show = true
end
```

With that turned on, you'll see the **found** layers that will be used:
