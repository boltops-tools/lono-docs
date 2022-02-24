## Usage

To install the components, run:

    $ lono bundle
    Exporting vendor/blueprints/ec2
    Exporting vendor/configsets/httpd
    Exporting vendor/extensions/ec2

Components are downloaded to your `vendor/blueprints`, `vendor/configsets`, `vendor/extensions` folders. The components in `vendor` is sourced same way as if they were defined in `app`. This is because Lono considers multiple lookup paths. Docs: [Lookup Paths]({% link _docs/blueprints/lookups.md %})

{% include lonofile/lockfile.md %}
