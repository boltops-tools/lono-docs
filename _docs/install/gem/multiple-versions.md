---
title: Installing and Using Multiple Versions of Lono
nav_text: Multiple Versions
category: gem
order: 1
---

If you're interested in running multiple or different versions of lono on the same machine, this page can help.

## How to Use Multiple Versions: Short Answer

The short answer to running different versions of lono is always to use the lono version that's in `Gemfile.lock`. You do this with `bundle exec`. Examples:

    $ grep '"lono"' Gemfile
    gem "lono", '~> 7.0.0'
    $ bundle # to ensure version is installed and Gemfile.lock is up-to-date
    $ grep '^  lono ' Gemfile.lock
      lono (~> 7.0.0)
    $ bundle exec lono -v
    7.0.0
    $

Change lono version in Gemfile:

    $ grep '"lono"' Gemfile
    gem "lono", '~> 8.0.0'
    $ bundle
    $ grep '^  lono ' Gemfile.lock
      lono (~> 8.0.0)
    $ bundle exec lono -v
    8.0.0
    $

To avoid having to remember to type `bundle exec`, you can use a [shim]({% link _docs/install/shim.md %}).

## Shim Wrapper

If have multiple versions of lono on the same system, you should always use the `bundle exec` command when you're inside the Lono project. This ensures that the lono version in the project's `Gemfile.lock` is used.  Typing `bundle exec` can get old quick, so you can use a [shim wrapper]({% link _docs/install/shim.md %}) to save yourself previous finger-typing energy.
