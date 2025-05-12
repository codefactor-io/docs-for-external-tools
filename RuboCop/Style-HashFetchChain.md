Pattern: Use of `fetch(identifier, nil)`

Issue: -

## Description

When `fetch(identifier, nil)` calls are chained on a hash, the expectation is that each step in the chain returns either `nil` or another hash, and in both cases, these can be simplified with a single call to dig with multiple arguments.

Use `Hash#dig` instead of chaining potentially null fetch calls.

## Examples

```ruby
# bad
hash.fetch('foo', nil)&.fetch('bar', nil)

# bad
# earlier members of the chain can return `{}` as long as the final `fetch`
# has `nil` as a default value
hash.fetch('foo', {}).fetch('bar', nil)

# good
hash.dig('foo', 'bar')

# ok - not handled by the cop since the final `fetch` value is non-nil
hash.fetch('foo', {}).fetch('bar', {})
```

## Further Reading

* [RuboCop - Style/HashFetchChain](https://docs.rubocop.org/rubocop/cops_style.html#stylehashfetchchain)
