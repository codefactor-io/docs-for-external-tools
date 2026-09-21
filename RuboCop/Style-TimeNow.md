Pattern: Use of `Time.new` without arguments

Issue: -

## Description

Checks for `Time.new` without arguments, which is an implicit way to retrieve the current system time. Prefer the more explicit `Time.now`.

## Examples

```ruby
# bad
Time.new

# good
Time.now

# good - `Time.new` with arguments constructs a specific time
Time.new(2026, 8, 19)
```

## Further Reading

* [RuboCop - Style/TimeNow](https://docs.rubocop.org/rubocop/latest/cops_style.html#styletimenow)
* [Ruby Style Guide - Time.now](https://rubystyle.guide/#time-now)
