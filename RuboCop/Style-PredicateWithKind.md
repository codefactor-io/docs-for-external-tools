Pattern: Missing use of predicate with kind check

Issue: -

## Description

Looks for uses of `any?`, `all?`, `none?`, or `one?` with a block containing only an `is_a?`, `kind_of?`, or `instance_of?` check, and suggests using the predicate method with the class argument directly.

## Examples

```ruby
# bad
array.any? { |x| x.is_a?(Integer) }
array.all? { |x| x.kind_of?(String) }
array.none? { |x| x.is_a?(Float) }
array.one? { |x| x.instance_of?(Symbol) }

# good
array.any?(Integer)
array.all?(String)
array.none?(Float)
array.one?(Symbol)
```

## Further Reading

* [RuboCop - Style/PredicateWithKind](https://docs.rubocop.org/rubocop/latest/cops_style.html#stylepredicatewithkind)
