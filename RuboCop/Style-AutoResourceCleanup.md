Pattern: Auto resource cleanup

Issue: -

## Description

This cop checks for cases when you could use a block
accepting version of a method that does automatic
resource cleanup.

### Example

```ruby
# bad
f = File.open('file')

# good
File.open('file') do |f|
  ...
end
```

## Further Reading

* [RuboCop - Style/AutoResourceCleanup](https://rubocop.readthedocs.io/en/latest/cops_style/#styleautoresourcecleanup)