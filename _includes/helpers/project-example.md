## Example Project Helper

You define helpers in within a subfolder in the `app/helpers` folder as a Ruby module.  The module name should be the camelized version of the file name. Here's an example where a helper is used to set default properties and remove the need to set the resource type:

app/helpers/bucket/bucket_helper.rb

```ruby
module BucketHelper
  def bucket(logical_id)
    param = "#{logical_id}Name"
    properties = {
      BucketName: ref(param, Conditional: true),
      AccessControl: "Private",
    }
    resource(logical_id, "AWS::S3::Bucket", properties)
  end
end
```

You can use the helper in your template:

app/blueprints/demo/template.rb

```ruby
parameter("BucketName", Conditional: true)
bucket("Bucket")
output("BucketName", ref("Bucket"))
```

Note: Project-level helpers must be within a subfolder. For example, `app/helpers/bucket/bucket_helper.rb` works and `app/helpers/bucket_helper.rb` will not work.

## Generate Helper

You can generate a starter helper module with:

    lono new helper project HELPER_NAME # general form
    lono new helper project bucket      # bucket => bucket_helper.rb
    lono new helper project             # helper name defaults to custom => custom_helper.rb

Example:

    $ lono new helper project bucket
    => Generating bucket_helper.rb
          create  app/helpers/bucket
          create  app/helpers/bucket/bucket_helper.rb
    $

## Vendor Helpers and Precedence

Project-level helpers can also be defined in `vendor/helpers`.  This works with the [Lonofile]({% link _docs/lonofile.md %}).  The order of precedence is:

    app/blueprints/demo/helpers # highest precedence
    app/helpers
    vendor/helpers              # lowest precedence
