Pattern: Redundant `Array#flatten`

Issue: -

## Description

Checks for redundant calls of `Array#flatten`.

`Array#join` joins nested arrays recursively, so flattening an array beforehand is redundant.

## Examples

```ruby
# bad
# bad
x.flatten.join
x.flatten(1).join

# good
x.join
```

## Further Reading

* [RuboCop - Style/RedundantArrayFlatten](https://docs.rubocop.org/rubocop/cops_style.html#styleredundantarrayflatten)