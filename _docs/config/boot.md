---
title: Boot Hooks
nav_text: Boot Hooks
category: config
order: 5
---

If you need to hook into the Lono boot process super-early on, Lono boot hooks are designed for that.

* They run very early in the Lono boot process.
* They are useful for setting shared global values like env vars.
* Boot hooks are ruby files that get required. It's nice and simple. There's no interface to learn.

## Hooks

Lono will searches 2 files in the `config` folder. If the files exist, they will be ran in this order.

1. **config/boot.rb**: Always runs.
2. **config/boot/LONO_ENV.rb**: Runs based on the env. IE: `LONO_ENV=dev` => `config/boot/dev.rb`

Both files are required and ran if they both exists. Since the `LONO_ENV` one runs second, it can be used to override previously set values.

## Example: Default LONO_ENV

If you prefer a different default than `LONO_ENV=dev`.

config/boot.rb

```ruby
ENV['LONO_ENV'] ||= 'prod'
```

This changes the default for everyone using the project, but still allows them to control the default by adding `export LONO_ENV=dev` to their `~/.bash_profile`.

## Example: Auto-Switch AWS_PROFILE

One useful example is switching `AWS_PROFILE` based on the `LONO_ENV`. Example:

config/boot/dev.rb

```ruby
ENV['AWS_PROFILE'] = 'dev'
```

This example is for AWS, but you can can do similiar switch logic with `GOOGLE_APPLICATION_CREDENTIALS`, etc.

## Boot Source

Please refer to the boot source code for more details: [lono/booter.rb](https://github.com/boltops-tools/lono/blob/master/lib/lono/booter.rb)
