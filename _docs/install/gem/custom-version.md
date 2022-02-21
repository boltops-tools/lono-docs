---
title: How to Use Custom Version of Lono
nav_text: Custom Version
category: gem
order: 2
---

If you want or need to run a forked version of lono, here's how:

## Change Version Number

First, clone down the source and change version number so you can identify that it's a custom version.  Clone down the project:

    $ git clone https://github.com/boltops-tools/lono

Update [lib/lono/version.rb](https://github.com/boltops-tools/lono/blob/master/lib/lono/version.rb) so you'll be able to tell that it's a custom build.  For example:

```ruby
module Lono
  VERSION = "8.0.0.custom"
end
```

There are 2 ways to use the custom version:

1. Gemfile: Forked Git Source
2. Gem Package: Build and Install

## Gemfile: Forked Git Source

Point `lono ` to use your repo with the forked version.  Example:

Gemfile:

```ruby
source "https://rubygems.org"
gem 'lono', git: 'https://github.com/REPO/lono', branch: "master"
```

Remember to change `REPO`, to your repo name.

Then run:

    bundle

## Gem Package: Build and Install

Build the gem package:

    $ bundle
    $ rake build
    pkg/lono-8.0.0.custom.gem

The produced `.gem` file can used to install the gem. You can install it locally:

    $ gem install pkg/lono-8.0.0.custom.gem
    $ lono -v
    8.0.0.custom

Or on any machine with Ruby installed. You can copy it to the machine, ssh into it, and install the custom gem:

    $ scp pkg/lono-8.0.0.custom.gem user@server.com:
    $ ssh user@server.com
    $ gem install lono-8.0.0.custom.gem
    $ lono -v
    8.0.0.custom

## Contributing

Learning how to run a forked version of lono allows you to make changes to the framework. Consider improving lono by submitting a Pull Request. See: [Contributing]({% link _docs/contributing.md %}).
