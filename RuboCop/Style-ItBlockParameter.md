Pattern: Malformed `it` block parameter

Issue: -

## Description

Checks for blocks with one argument where `it` block parameter can be used.

It provides three `EnforcedStyle` options:

    `allow_named_parameter` (default) …​ Detects only numbered block parameters.

    `always` …​ Always uses the `it` block parameter.

    `disallow` …​ Disallows the `it` block parameter.


## Examples

```ruby
# EnforcedStyle: allow_named_parameter (default)

# bad
block { do_something(_1) }

# good
block { do_something(it) }
block { |named_param| do_something(named_param) }
```

## Further Reading

* [RuboCop - Style/ItBlockParameter](https://docs.rubocop.org/rubocop/cops_style.html#styleitblockparameter)