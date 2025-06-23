Pattern: Empty string inside interpolation

Issue: -

## Description

Empty strings are a meaningless outcome inside of string interpolation.

## Examples

### EnforcedStyle: trailing_conditional (default)

```ruby
# bad
"#{condition ? 'foo' : ''}"

# good
"#{'foo' if condition}"

# bad
"#{condition ? '' : 'foo'}"

# good
"#{'foo' unless condition}"
```

### EnforcedStyle: ternary

```ruby
# bad
"#{'foo' if condition}"

# good
"#{condition ? 'foo' : ''}"

# bad
"#{'foo' unless condition}"

# good
"#{condition ? '' : 'foo'}"
```

## Further Reading

* [RuboCop - Style/EmptyStringInsideInterpolation](https://docs.rubocop.org/rubocop/cops_style.html#styleemptystringinsideinterpolation)
