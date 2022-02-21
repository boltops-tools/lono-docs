---
title: Gem Installation
---

To install lono via RubyGems.

    gem install lono --prerelease

This will install a lono v8 rc version.

Ruby 3.0 and above is recommended.

The nice thing about this installation method is that is the standard way to install Ruby libraries and gems. It integrates with your existing Ruby installation. And you have the most control over the installation.

If you're looking for Ruby installation help: [Ruby Install]({% link _docs/install/ruby.md %}) docs.

## Updating

To update lono, update project's `Gemfile` and use bundler. Update:

Gemfile

```ruby
source "https://rubygems.org"
gem "lono", '~> 8.0.0' # <= UPDATE THIS LINE
```

Then run:

    bundle update

Bundler will update lono and other dependencies to the latest.

## Shim

With a gem install, it's recommended to generate a [shim]({% link _docs/install/shim.md %}) so you don't have to remember to type `bundle exec` when running `lono` within the Lono project folder.
