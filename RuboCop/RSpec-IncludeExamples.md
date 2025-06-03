Pattern: Use of `include_examples`

Issue: -

## Description

`include_examples`, unlike `it_behaves_like`, does not create its own context. As such, using `subject`, `let`, `before`/`after`, etc. within shared examples included with `include_examples` can have unexpected behavior and side effects.

Prefer using `it_behaves_like` instead.


## Examples

```ruby
# bad
include_examples 'examples'

# good
it_behaves_like 'examples'
```

## Further Reading

* [RSpec - RSpec/IncludeExamples](https://docs.rubocop.org/rubocop-rspec/cops_rspec.html#rspecincludeexamples)
