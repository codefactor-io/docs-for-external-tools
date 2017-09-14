Pattern: Layout/BlockEndNewline

Issue: -

## Description

This cop checks whether the end statement of a do..end block
is on its own line.

### Example

```ruby
# bad
blah do |i|
  foo(i) end

# good
blah do |i|
  foo(i)
end

# bad
blah { |i|
  foo(i) }

# good
blah { |i|
  foo(i)
}
```

## Further Reading

* [RuboCop - Layout/BlockEndNewline](https://rubocop.readthedocs.io/en/latest/cops_layout/#layoutblockendnewline)