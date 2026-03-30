Pattern: Missing use of `grep`/`grep_v`

Issue: -

## Description

Looks for places where a subset of an Enumerable (array, range, set, etc.; see note below) is calculated based on a range check, and suggests `grep` or `grep_v` instead.

## Examples

```ruby
# bad (select or find_all)
array.select { |x| x.between?(1, 10) }
array.select { |x| (1..10).cover?(x) }
array.select { |x| (1..10).include?(x) }

# bad (reject)
array.reject { |x| x.between?(1, 10) }

# bad (find or detect)
array.find { |x| x.between?(1, 10) }
array.detect { |x| (1..10).cover?(x) }

# bad (negative form)
array.reject { |x| !x.between?(1, 10) }
array.find { |x| !(1..10).cover?(x) }

# good
array.grep(1..10)
array.grep_v(1..10)
array.grep(1..10).first
array.grep_v(1..10).first
```

## Further Reading

* [RuboCop - Style/SelectByRange](https://docs.rubocop.org/rubocop/latest/cops_style.html#styleselectbyrange)
