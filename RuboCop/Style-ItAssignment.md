Pattern: Assignment to local `it` variable

Issue: -

## Description

Checks for assignments to a local `it` variable inside a block where `it` can refer to the first anonymous parameter as of Ruby 3.4.

Although Ruby allows reassigning `it` in these cases, it could cause confusion if `it` is used as a block parameter elsewhere. For consistency, this also applies to numblocks and blocks with parameters, even though `it` cannot be used in those cases.

## Examples

```ruby
# bad
foo { it = 5 }
foo { |bar| it = bar }
foo { it = _2 }

# good - use a different variable name
foo { var = 5 }
foo { |bar| var = bar }
foo { bar = _2 }
```


## Further Reading

* [RuboCop - Style/ItAssignment](https://docs.rubocop.org/rubocop/cops_style.html#styleitassignment)