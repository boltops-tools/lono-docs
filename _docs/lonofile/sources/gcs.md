---
title: GCS buckets
nav_text: GCS
categories: sources
order: 5
---

## Example

Lonofile

```ruby
blueprint "demo1", source: "gcs::https://www.googleapis.com/storage/v1/demo-google-bucket/blueprints/demo-blueprint.zip//subfolder"
blueprint "demo2", source: "gcs::https://www.googleapis.com/storage/v1/demo-google-bucket/blueprints/demo-blueprint.tgz//subfolder"
```

Running:

    lono bundle

Will download the blueprints to:

    vendor/blueprints/demo1
    vendor/blueprints/demo2

## Install

In order to use gcs as a lono bundler source, please add the `google-cloud-storage` gem to your Lono project's Gemfile and run bundle.

    To add the gem to your Gemfile, you can run:

        bundle add google-cloud-storage

    Then download blueprints in defined your Lonofile with:

        lono bundle

{% include lonofile/archive-support.md %}
