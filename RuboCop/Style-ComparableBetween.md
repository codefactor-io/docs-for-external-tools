Pattern: Missing use of `Comparable#between?`

Issue: -

## Description

Checks for logical comparison which can be replaced with `Comparable#between?`.

## Examples

```ruby
# bad
x >= min && x <= max

# bad
x <= max && x >= min

# good
x.between?(min, max)
```

## Further Reading

* [RuboCop - Style/ComparableBetween](https://docs.rubocop.org/rubocop/cops_style.html#stylecomparablebetween)
