---
title: Condition Functions
categories: intrinsic-function
desc: You can use intrinsic functions, such as `Fn::If`, `Fn::Equals`, and `Fn::Not`, to conditionally create stack resources. These conditions are evaluated based on input parameters that you declare when you create or update a stack. After you define all your conditions, you can associate them with resources or resource properties in the Resources and Outputs sections of a template.
aws_text: Condition Functions
aws_link: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference-conditions.html
---

{{ page.desc }}

Lono supports [{{ page.aws_text }}]({{ page.aws_link }}).  Since most of these function names are Ruby keywords they must be called with a bang (!).

* equals
* and!
* if!
* not!
* or!

Examples follow:

## Example: equals

```ruby
condition("UseProdCondition",
  equals(ref("EnvironmentType"), "prod")
)
```

outputs:

```yaml
Conditions:
  UseProdCondition:
    Fn::Equals:
    - Ref: EnvironmentType
    - prod
```

## Example: and!

```ruby
condition("MyAndCondition",
  and!(equals("sg-mysggroup", ref("ASecurityGroup")), {Condition: "SomeOtherCondition"})
)
```

outputs:

```yaml
Conditions:
  MyAndCondition:
    Fn::And:
    - Fn::Equals:
      - sg-mysggroup
      - Ref: ASecurityGroup
    - Condition: SomeOtherCondition
```

## Example: if!

```ruby
condition("SecurityGroups",
  if!("CreateNewSecurityGroup", ref("NewSecurityGroup"), ref("ExistingSecurityGroup"))
)
```

outputs:

```yaml
Conditions:
  SecurityGroups:
    Fn::If:
    - CreateNewSecurityGroup
    - Ref: NewSecurityGroup
    - Ref: ExistingSecurityGroup
```

## Example: not!

```ruby
condition("MyNotCondition",
  not!(equals(ref("EnvironmentType"), "prod"))
)
```

outputs:

```yaml
Conditions:
  MyNotCondition:
    Fn::Not:
    - Fn::Equals:
      - Ref: EnvironmentType
      - prod
```

## Example: or!

```ruby
condition("MyOrCondition",
  or!(equals("sg-mysggroup", ref("ASecurityGroup")), {Condition: "SomeOtherCondition"})
)
```

outputs:

```yaml
Conditions:
  MyOrCondition:
    Fn::Or:
    - Fn::Equals:
      - sg-mysggroup
      - Ref: ASecurityGroup
    - Condition: SomeOtherCondition
```

{% include back_to/intrinsic_functions.md %}


