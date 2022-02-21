---
title: Change Infrastructure
---

Now that we have bucket created, let's modify it. Here's the template code again.

app/blueprints/demo/template.rb

```ruby
parameter("BucketName", Conditional: true)
parameter("AccessControl", Default: "Private")

resource("Bucket", "AWS::S3::Bucket",
  BucketName: ref("BucketName", Conditional: true),
  AccessControl: ref("AccessControl"),
)

output("BucketName", ref("Bucket"))
```

As you can see there's a `AccessControl` parameter. One way to update the infrastructure is to directly change the parameter in the `template.rb` file. However, it is better to use a parameters file and pass it to the CloudFormation call. Using parameters allow us create different environments with the same code.

To pass parameter values, you simply have to define `config/blueprints/demo/params` files. Lono automaticallys uses them according the `LONO_ENV` value. The default value is `LONO_ENV=dev`.

## Generate Starter Params Files

Lono can also generate starter params files for us with the `lono seed` command.

    $ lono seed demo
    Creating starter config files for demo
          create  config/blueprints/demo/params/dev.txt
    $

This produces:

config/blueprints/demo/params/dev.txt

    # AccessControl=Private
    # BucketName=

Lono uses the information from `output/demo/template.yml` to generate the starter params file.  It detected that all the parameters are optional, adds them with a leading comment.  We'll uncomment `AccessControl` and change it to `AccessControl=PublicRead`.

config/blueprints/demo/params/dev.txt

    AccessControl=PublicRead
    # BucketName=

Next, we'll update the infrastructure.
