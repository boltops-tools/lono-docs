## Example Helper

You define helpers in the blueprint's `helpers` folder as a Ruby module.  The module name should be the camelized version of the file name. Here's an example where a helper is used to set default properties and remove the need to set the resource type:

app/blueprints/demo/helpers/ec2_helper.rb

```ruby
module Ec2Helper
  def ec2_instance(logical_id, props={})
    default = {
      InstanceType: "t3.micro",
      ImageId: ref("AmiId"),
    }
    props.reverse_merge!(default)

    resource("Instance", "AWS::EC2::Instance", props)
  end

  def security_group(logical_id, props={})
    resource("SecurityGroup", "AWS::EC2::SecurityGroup", props)
  end
end
```

You can use the helper in your template:

app/blueprints/demo/template.rb

```ruby
ec2_instance("Instance",
  SecurityGroupIds: [get_att("SecurityGroup.GroupId")]
)
security_group("SecurityGroup",
  GroupDescription: "demo security group",
)
```

## Generate Helper

You can generate a starter helper module with:

    lono new helper --name NAME --blueprint BLUEPRINT # general form
    lono new helper --name custom --blueprint demo
    lono new helper --blueprint demo # also works --name defaults to custom

Example:

    $ lono new helper --blueprint demo
    => Generating helper: custom
          create  app/blueprints/demo/helpers/custom_helper.rb
    $
