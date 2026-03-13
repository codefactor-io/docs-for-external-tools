Pattern: Missing use of `Array#join`

Issue: -

## Description

Checks for map `{ |x| x.to_s }.join` and similar calls where the `map` is redundant because `Array#join` implicitly calls `#to_s` on each element.

## Examples

```
# bad
array.map(&:to_s).join(', ')

# bad
array.map { |x| x.to_s }.join(', ')

# bad
array.collect(&:to_s).join

# good
array.join(', ')

# good
array.join
```

## Further Reading

* [RuboCop - Style/MapJoin](https://docs.rubocop.org/rubocop/cops_style.html#stylecollectioncompact)
