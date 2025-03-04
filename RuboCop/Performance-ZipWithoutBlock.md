Pattern: Use of `map { |id| [id] }`

Issue: -

## Description

Checks for `map { |id| [id] }` and suggests replacing it with `zip`.

## Examples

```ruby
# bad
[1, 2, 3].map { |id| [id] }

# good
[1, 2, 3].zip
```

## Further Reading

* [RuboCop - Performance/ZipWithoutBlock](https://docs.rubocop.org/rubocop-performance/cops_performance.html#performancezipwithoutblock)
