Pattern: Missing use of `to_h`

Issue: -

## Description

Checks for `each_with_object`, `inject`, and `reduce` calls that build a hash from an enumerable, where `to_h` with a block could be used instead.

## Examples

```ruby
# bad
array.each_with_object({}) { |elem, hash| hash[elem.id] = elem.name }

# bad
array.inject({}) { |hash, elem| hash[elem.id] = elem.name; hash }

# bad
array.reduce({}) { |hash, elem| hash[elem.id] = elem.name; hash }

# bad
array.each_with_object({}) { |elem, hash| hash[elem] = elem.to_s }

# good
array.to_h { |elem| [elem.id, elem.name] }

# good
array.to_h { |elem| [elem, elem.to_s] }
```

## Further Reading

* [RuboCop - Style/ReduceToHash](https://docs.rubocop.org/rubocop/latest/cops_style.html#stylereducetohash)
