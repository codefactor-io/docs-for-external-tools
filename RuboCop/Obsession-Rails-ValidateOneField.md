Pattern: Multiple fields in single `validate` call

Issue: -

## Description

Checks for `validates` callbacks with multiple fields. One field per `validates` makes the validation extra clear.

## Examples

Example of **incorrect** code:
```ruby
validates :name, :status, presence: true
```

Example of **correct** code:
```ruby
validates :name, presence: true
validates :status, presence: true
```