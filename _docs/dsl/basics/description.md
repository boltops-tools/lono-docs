---
title: Description
category: dsl-basics
desc: The optional Description section enables you to include comments about your
  template. The Description must follow the AWSTemplateFormatVersion section.
aws_text: Description
aws_link: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-description-structure.html
---

{{ page.desc }}

The `description` method maps to the CloudFormation Template Anatomy [{{ page.aws_text }}]({{ page.aws_link }}).

# Example Snippet


```ruby
description "AutoScaling CloudFormation template"
```

## Output

```yaml
Description: AutoScaling CloudFormation template
```

{% include back_to/dsl-basics.md %}


