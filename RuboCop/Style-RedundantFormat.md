Pattern: Redundant `format`/`sprintf`

Issue: -

## Description

Checks for calls to `Kernel#format` or `Kernel#sprintf` that are redundant.

Calling `format` with only a single string or constant argument is redundant, as it can be replaced by the string or constant itself.

Also looks for `format` calls where the arguments are literals that can be inlined into a string easily. This applies to the `%s`, `%d`, `%i`, `%u`, and `%f` format specifiers.

## Examples

```ruby
# bad
format('the quick brown fox jumps over the lazy dog.')
sprintf('the quick brown fox jumps over the lazy dog.')

# good
'the quick brown fox jumps over the lazy dog.'

# bad
format(MESSAGE)
sprintf(MESSAGE)

# good
MESSAGE

# bad
format('%s %s', 'foo', 'bar')
sprintf('%s %s', 'foo', 'bar')

# good
'foo bar'
```

## Further Reading

* [RuboCop - Style/RedundantFormat](https://docs.rubocop.org/rubocop/cops_style.html#styleredundantformat)
