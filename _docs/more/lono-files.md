---
title: Lono Uploaded Files
nav_text: Uploaded Files
categories: more
order: 1
---

Lono can automatically upload files to s3 and make them available to reference in your CloudFormation templates as a part of [lono up]({% link _reference/lono-up.md %}). This is particularly useful for Lambda functions.

## Lambda Function Example

The file or files get zipped and uploaded to s3.

app/blueprints/demo/files/index.rb

```ruby
def lambda_handler(event:, context:)
  puts "hello"
end
```

In the template definition, you reference the uploaded file like so

app/blueprints/demo/template.rb

```ruby
resource("Function", "AWS::Lambda::Function",
  Code: {
    S3Bucket: files_bucket,
    S3Key: files("files/index.rb"), # use files/index.rb
  },
  Handler: "index.lambda_handler",
  Role: get_att("LambdaExecutionRole.Arn"),
  Runtime: "ruby2.7",
  Timeout: "300"
)
```

The files only get uploaded if the method `files` is called in your templates. Lono zip ups the file to work with Lambda.

## Zipping Folders

If pass `files` a folder instead of a file, lono zips up the entire contents within the folder to work with Lambda.

## Templating Support

ERB Template is also supported in app files. To activate ERB support, add a `.tt` extension to the file name. Lono processes the `.tt` files as ERB files and the `.tt` extension will be removed from the resulting final file.  You have access to your [Variables]({% link _docs/config/variables.md %}) and [Helpers]({% link _docs/helpers.md %}).

Example:

app/blueprints/demo/files/index.rb.tt:

```ruby
require 'json'

def lambda_handler(event:, context:)
  # <%= "comment is from erb" %>
  { statusCode: 200, body: JSON.generate('Hello from Lambda!') }
end
```

Results in:

app/blueprints/demo/files/index.rb:

```ruby
require 'json'

def lambda_handler(event:, context:)
  # comment is from erb
  { statusCode: 200, body: JSON.generate('Hello from Lambda!') }
end
```


