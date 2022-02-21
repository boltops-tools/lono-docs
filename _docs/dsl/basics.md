---
title: DSL Basics
---

Here are the top-level DSL methods.

{% assign docs = site.docs | where: "categories","dsl-basics" %}
Lono DSL | CloudFormation | Description
--- | --- | ---
{% for doc in docs -%}
[{{ doc.title }}]({{ doc.url }}) | [{{ doc.aws_text }}]({{ doc.aws_link }}) | {{ doc.desc }}
{% endfor %}

The main methods correspond to sections of the [CloudFormation anatomy sections](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-anatomy.html).

The DSL provides full access to creating custom CloudFormation stacks and AWS resources.  You can also wrap the DSL methods with your own [Helpers]({% link _docs/helpers/custom.md %}). This helps you keep your code concise and more readable.
