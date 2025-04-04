Pattern: Missing validation method prefix

Issue: -

## Description

Checks for validation methods that do not start with `validate_`.

## Examples

Example of **incorrect** code:
```ruby
validate :at_least_one_admin
```

Example of **correct** code:
```ruby
validate :validate_at_least_one_admin
```