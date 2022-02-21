---
title: Format Version
category: dsl-basics
desc: The optional AWSTemplateFormatVersion section identifies the capabilities of the template.
aws_text: AWSTemplateFormatVersion
aws_link: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/format-version-structure.html
---

{{ page.desc }}

The `aws_template_format_version` method maps to the CloudFormation Template Anatomy [{{ page.aws_text }}]({{ page.aws_link }}).

# Example Snippet


```ruby
aws_template_format_version "2010-09-09"
```

## Output

```yaml
AWSTemplateFormatVersion: '2010-09-09'
```

{% include back_to/dsl-basics.md %}


