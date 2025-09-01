Pattern: String argument in `order` method

Issue: -

## Description

Prefer symbol arguments over strings in `order` method.

## Examples

```ruby
# bad
User.order('name')
User.order('name DESC')

# good
User.order(:name)
User.order(name: :desc)
```

## Further Reading

* [RuboCop - Rails/OrderArguments](https://docs.rubocop.org/rubocop-rails/cops_rails.html#railsorderarguments)
