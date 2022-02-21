---
title: Shim Wrapper
---

Lono projects have a `Gemfile.lock`. This file ensures that gem dependencies for are pinned. To use it, you run `bundle exec lono`. It can be annoying to remember typing `bundle exec`, though. Using a shim spares you from having to remember this, saving you precious finger-typing energy.

## Using a Shim

A shim wrapper ensures that `bundle exec` is prepended in front of lono when you're within a project. You only have to set up the shim once. You can generate a shim with:

    $ lono new shim
          create  /usr/local/bin/lono
           chmod  /usr/local/bin/lono

The shim looks something like this:

    #!/bin/bash
    if [ -f config/app.rb ]; then
      exec bundle exec lono "$@"
    else
      exec lono "$@"
    fi

By default, the shim is written to `/usr/local/bin/lono`. As long as `/usr/local/bin` is early enough in your system `$PATH`, you can type `lono` instead of `bundle exec lono`.

You can change the path with the `--path` option. More info: [lono new shim]({% link _reference/lono-new-shim.md %}).

The shim wrapper generally work for most systems, it might require adjustments depending on your system.

## Rbenv Shim Slowness

If you are using rbenv, it can be [slow](https://github.com/rbenv/rbenv/issues/70) on some systems. You may want to consider replacing the shim that rbenv generates with a faster one. Here's an example:

~/.rbenv/shims/lono

    #!/usr/bin/env bash
    EXE=$(gem which lono | sed 's|lib/lono.rb|exe/lono|')
    if [ -f config/app.rb ]; then
      exec bundle exec $EXE "$@"
    else
      exec $EXE "$@"
    fi

## Multiple Lono Versions

A shim is recommended when you have multiple versions of Lono installed on the same system. See: [Multiple Lono Versions]({% link _docs/install/gem/multiple-versions.md %})

## Long Answer: Why bundle exec?

The key to understanding why `bundle exec` is needed sometimes is understadning Ruby, bundler, and system paths work. You see, when you run **any** cli command with `bundle exec` pretended, it affects the system load path.

Example without:

    lono version

Example with:

    bundle exec lono version

Using `bundle exec` adjusts the load path. The load paths are adjusted to ensure that the exact versions specified in `Gemfile.lock` are used. This includes, not only lono, but all Ruby gem dependencies.

When you don't use `bundle exec`, the gem versions used are more dependent how on your environment is configured. In this case, Ruby has little choice but to make some assumptions and uses the first gems found based on your system load path.  Usually, the latest gem versions installed on the system are used.

Lono actually calls `bundle exec` super early on [internally](https://github.com/boltops-tools/lono/blob/master/lib/lono/autoloader.rb#L2). This helps mitigate dependencies graph resolution issues. But Lono is only able to pin at that point and won't work for all cases. Sometimes gems must be pinned even before Lono is loaded.

It won't work when there's a later version of lono installed on the system, and your `Gemfile.lock` pins a different lono version. In this case, you'll need to use `bundle exec` or uninstall other versions of lono from your system.

## Bundler already activated Warnings

If you are seeing an error that says a gem dependency is "already activated", for example:

    You have already activated faraday 1.7.0, but your Gemfile requires faraday 0.17.4. Prepending `bundle exec` to your command may solve this.

Prepending `bundle exec` should resolve the issue. Or you can generate a [shim]({% link _reference/lono-new-shim.md %}) as described above.
