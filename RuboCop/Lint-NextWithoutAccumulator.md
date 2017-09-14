Pattern: Lint/NextWithoutAccumulator

Issue: -

## Description

Don't omit the accumulator when calling `next` in a `reduce` block.

### Example

```ruby
# bad

result = (1..4).reduce(0) do |acc, i|
  next if i.odd?
  acc + i
end
```
```ruby
# good

result = (1..4).reduce(0) do |acc, i|
  next acc if i.odd?
  acc + i
end
```

## Further Reading

* [RuboCop - Lint/NextWithoutAccumulator](https://rubocop.readthedocs.io/en/latest/cops_lint/#lintnextwithoutaccumulator)