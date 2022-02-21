## Params and Variables Same Lookup Strategy

Params and variables follow the same lookup strategy. So it makes sense to have them located in a similar structure. Example:

    config/demo/params/dev/my-stack.txt
    config/demo/variables/dev/my-stack.rb

The deploy command would be:

    lono up my-stack --blueprint demo

## The `--config` Option

The `--param` and `--variable` option allow you to override each specific config file lookup.  The `--config` option is a convenience option that sets both `--param` and `--variable` at the same time.  Example:

    lono up my-stack --blueprint demo --config test

Is the same as:

    lono up my-stack --blueprint demo --param test --variable test
