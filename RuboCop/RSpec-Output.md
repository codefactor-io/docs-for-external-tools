Pattern: Use of output call

Issue: -

## Description

Checks for the use of output calls like puts and print in specs.

## Examples

```ruby
# bad
puts 'A debug message'
pp 'A debug message'
print 'A debug message'
```

## Further Reading

* [RSpec - RSpec/Output](https://docs.rubocop.org/rubocop-rspec/cops_rspec.html#rspecoutput)