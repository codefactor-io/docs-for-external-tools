Pattern: Lint/Debugger

Issue: -

## Description

This cop checks for calls to debugger or pry.

### Example

```ruby
# bad (ok during development)

# using pry
def some_method
  binding.pry
  do_something
end
```
```ruby
# bad (ok during development)

# using byebug
def some_method
  byebug
  do_something
end
```
```ruby
# good

def some_method
  do_something
end
```

## Further Reading

* [RuboCop - Lint/Debugger](https://rubocop.readthedocs.io/en/latest/cops_lint/#lintdebugger)