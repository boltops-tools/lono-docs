---
title: Lambda Layers
categories: more
order: 2
---

Lono can build and upload Lambda Layers.

## Lambda Layer Example

Here's an example to demonstrate how lono can help build a Lambda Layer.

First, here's a Lambda function in Ruby.

app/blueprints/demo/files/lambda-function/index.rb:

```ruby
def lambda_handler(event:, context:)
  puts "event: #{JSON.dump(event)}"
  puts "context: #{JSON.dump(context)}"
  {message: "hello world"}
end
```

And a `Gemfile` with dependencies for the Lambda Layer.

app/blueprints/demo/files/lambda-function/Gemfile

```ruby
source "https://rubygems.org"
gem "s3-secure"# Example gem. Lambda Layer cannot be empty and requires at least one dependency.
```

Next, we'll create a Lambda function and Lambda Layer.

app/blueprints/demo/template.rb

```ruby
resource("Function", "AWS::Lambda::Function",
  Code: {
    S3Bucket: files_bucket,
    S3Key: files("files/lambda-function"), # app/blueprints/demo/files/lambda-function
  },
  Description: "Lambda Function",
  Handler: "index.lambda_handler",
  Layers: [ref("LayerVersion")],
  Role: get_att("LambdaExecutionRole.Arn"),
  Runtime: "ruby2.7",
  Timeout: "300",
)

resource("LayerVersion", "AWS::Lambda::LayerVersion",
  CompatibleRuntimes: ["ruby2.7"],
  Content: {
    S3Bucket: files_bucket,
    S3Key: files("files/lambda-function", layer: "ruby") # <= NOTE: layer: "ruby"
  },
  Description: "lambda layer",
  LayerName: "lambda-layer", # if not named, then it defaults to the logical id
  LicenseInfo: "Nonstandard"
)
```

The `layer: "ruby` option tells Lono to build and package up the files in `files/lambda-function` a Lambda Layer.

IMPORANT: Run `bundle` in the `app/blueprints/demo/files/lambda-function` folder to generate an updated `Gemfile.lock` file. Otherwise, you'll get an error complaining about missing dependencies when the Lambda function tries to run.  Lambda uses `Gemfile.lock`.

## Lambda Layers for Other Languages

Currently, Lono does not automatically build Lambda Layers for other languages to the same degree of convenience as Ruby. Will welcome and review PRs.

You have to add the files directly to the `app/blueprints/demo/files/lambda-function` folder for other languages. Lono uploads files in that folder. You will have to provide the dependency artifacts directly. Example:

app/blueprints/demo/template.rb

```ruby
resource("LayerVersion", "AWS::Lambda::LayerVersion",
  CompatibleRuntimes: ["python3.8"],
  Content: {
    S3Bucket: files_bucket,
    S3Key: files("python-layer") # <= NOTE: no layer option pass
  },
  Description: "python layer",
  LayerName: "python-layer", # if not named, then it defaults to the logical id
  LicenseInfo: "Nonstandard"
)
```
