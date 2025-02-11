Pattern: Missing use of `Hash#slice`

Issue: -

## Description

Checks for usages of `Hash#reject`, `Hash#select`, and `Hash#filter` methods that can be replaced with `Hash#slice` method.

## Examples

```ruby
# bad
{foo: 1, bar: 2, baz: 3}.select {|k, v| k == :bar }
{foo: 1, bar: 2, baz: 3}.reject {|k, v| k != :bar }
{foo: 1, bar: 2, baz: 3}.filter {|k, v| k == :bar }
{foo: 1, bar: 2, baz: 3}.select {|k, v| k.eql?(:bar) }

# bad
{foo: 1, bar: 2, baz: 3}.select {|k, v| %i[bar].include?(k) }
{foo: 1, bar: 2, baz: 3}.reject {|k, v| !%i[bar].include?(k) }
{foo: 1, bar: 2, baz: 3}.filter {|k, v| %i[bar].include?(k) }

# bad
{foo: 1, bar: 2, baz: 3}.select {|k, v| !%i[bar].exclude?(k) }
{foo: 1, bar: 2, baz: 3}.reject {|k, v| %i[bar].exclude?(k) }

# bad
{foo: 1, bar: 2, baz: 3}.select {|k, v| k.in?(%i[bar]) }
{foo: 1, bar: 2, baz: 3}.reject {|k, v| !k.in?(%i[bar]) }

# good
{foo: 1, bar: 2, baz: 3}.slice(:bar)
```

## Further Reading

* [RuboCop - Style/HashSlice](https://docs.rubocop.org/rubocop/cops_style.html#stylehashslice)
