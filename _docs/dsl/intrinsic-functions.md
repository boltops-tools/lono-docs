---
title: Intrinsic Functions
---

Lono provides helper methods that map to [CloudFormation Intrinsic Functions](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference.html).

{% assign docs = site.docs | where: "categories","intrinsic-function" %}
Lono DSL | CloudFormation | Description
--- | --- | ---
{% for doc in docs -%}
[{{ doc.title }}]({{ doc.url }}) | [{{ doc.aws_text }}]({{ doc.aws_link }}) | {{ doc.desc }}
{% endfor %}
