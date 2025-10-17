Pattern: Suppressed exception in number conversion

Issue: -

## Description

Checks for cases where exceptions unrelated to the numeric constructors `Integer()`, `Float()`, `BigDecimal()`, `Complex()`, and `Rational()` may be unintentionally swallowed.

## Examples

```ruby
# bad
Integer(arg) rescue nil

# bad
begin
  Integer(arg)
rescue
  nil
end

# bad
begin
  Integer(arg)
rescue
end

# good
Integer(arg, exception: false)
```

## Further Reading

* [RuboCop - Lint/SuppressedExceptionInNumberConversion](https://docs.rubocop.org/rubocop/cops_lint.html#lintsuppressedexceptioninnumberconversion)
