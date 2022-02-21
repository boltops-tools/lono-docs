---
title: Lonofile Options
---

lono bundler has several configurable options. The options can apply at the:

1. **Component level**: These options apply at the component-level, so they specifically affect each component only.
2. **Lonofile level**: These options apply globally and affect the entire Lonofile.
3. **Config level**: These options generally apply globally and can affect the entire Lonofile or even CLI option behaviors like the `--lonofile` option.

The precedence of the options is also: 1, 2, and 3.

## 1. Component level

These options apply at the component-level, so they specifically affect each component only.

Name | Description | Default
--- |  --- | ---
export_to | Overrides the export_to Lonofile level option. IE: `vendor` With this one-off option, other components in the folder will not be purged. | nil
subfolder | The subfolder where the componentule lives within the repo. By default, the componentule code is assumed to be at the root of the git repo. You can change it with this setting. | nil
version | Lock componentule to specific version. Can also use: `branch`, `ref`, `sha`, `tag`. See [Version Locking]({% link _docs/lonofile/version-locking.md %}) | nil
clone_with | Protocol to use for `git clone` with private registry source. IE: `https` or `git`

Example Lonofile:

```ruby
blueprint "s3-bucket",   source: "org/s3-bucket", subfolder: "path/to/blueprint/s3-bucket"
configset "httpd", source: "org/httpd-configset", export_to: "app"
extension "ec2",   source: "boltops-tools/ec2-extension", version: "1.0.0"
```

## 2. Lonofile level

These options apply globally and affect the entire Lonofile.

Name | Description | Default
--- |  --- | ---
base_clone_url | Base clone url to use. | https://github.com/
export_to |  Where the components get exported to saved to. Note, be careful about changing this location to `app` as the default `export_purge=true` will remove this folder. It's safer to use `export_to` at the component-level.  | vendor
export_purge | Whether or not to remove all existing exported components folder first. If you disable this behavior, then you can manually clear components out yourself before installing. IE: `rm -r vendor/TYPE`. | true
clone_with | Protocol to use for `git clone` with private registry source. IE: `https` or `git`

Example Lonofile:

```ruby
base_clone_url "git@github.com:"  # override the default https://github.com/
export_to "app"        # override the default vendor
export_purge false                # override the default true
stack_options(purge: true)
```

## 3. Config level

These options generally apply globally and can affect the entire Lonofile or even CLI option behaviors like the `--Lonofile` option. With this approach, we are directly setting the lono bundler options: `TB.config`. Lono passes the [config.bundle]({% link _docs/config/reference.md %}) options straight through to `TB.config` and merges the settings:

Name | Description | Default
--- | --- | ---
base_clone_url | Base git url to use for cloning | https://github.com/
export_to | Where to export the components to. Can also be set with the env var `TB_EXPORT_PATH` | vendor
export_purge | Whether or not to purge all the components | true
logger | Logger instance. By default, lono bundler is set to use the same logger as Lono. | Lono.logger
lonofile | The Lonofile path. Can also be set with the env LB_LONOFILE | Lonofile
