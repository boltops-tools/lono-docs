---
title: Built-In Helpers
nav_text: Built-In
categories: helpers
order: 1
---

Here are some of the built-in helpers available in the Lono DSL:

Method | Description
--- | ---
default_subnets | Returns Array of default Subnet Ids. Useful for config params.
default_vpc | Returns default VPC id. Useful for config params.
extract_scripts | Generates a script that can be included in user_data scripts to extract `scripts` files. More info about the helper is in the [Extract Scripts docs]({% link _docs/helpers/builtin/extract-scripts.md %}).
key_pairs | Returns Array of Key Pairs. You can pass it a pattern to filter for keypairs. IE: `key_pairs(/default/).first`. Useful for config params.
[stack_output]({% link _docs/dsl/advanced/stack-output.md %}) | Returns the Stack output. IE: `stack_output("my-stack.OutputKey")`. Useful for [params files]({% link _docs/config/params.md %}).
stack_resource | Returns the Stack resource physical id. IE: `stack_resource("my-stack.LogicalId")`. Useful for [params files]({% link _docs/config/params.md %}).
[tags]({% link _docs/helpers/builtin/tags.md %}) | Converts a standard Ruby hash to the CloudFormation key, value structure.
user_data | Returns the script from the `app/user_data` folder as a String. Meant for user_data scripts.
[user_data_script]({% link _docs/helpers/builtin/user_data_script.md %}) | Path location of the script to be used along with the `user_data_script` helper.

The built-in helpers are defined in this this source code file: [dsl/evaluator/helpers](https://github.com/boltops-tools/lono/tree/master/lib/lono/builder/template/dsl/evaluator/helpers).

You can also create your own helpers with [Custom Helpers]({% link _docs/helpers/custom.md %}).
