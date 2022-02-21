---
title: Updating Lono
---

To update lono, you'll also need to update the pinned lono version in your Lono project's `Gemfile`. It looks something like this.

Gemfile

```ruby
gem "lono", '~> 8.0.0'
```

So to update terrapace to the next version can remove the version specificier `'~> 8.0.0'` entirely or update it to the version you wish.  Then run:

    bundle update lono

This generates a new `Gemfile.lock` that will pin a new lono version down. To confirm that the desired version of lono is being used:

    bundle info lono

## Updating Everything

If you want to update all dependencies. You can do that by running:

    bundle update

This updates all gems defined in the `Gemfile` and still try to keep implied dependencies generally pinned.

Often, you want to update all gems, including implied dependencies, completely. Blow away the `Gemfile.lock` and run `bundle update`. Example:

    rm -f Gemfile.lock
    bundle update

This generates a brand new `Gemfile.lock`. To see what versions are used:

    bundle list
