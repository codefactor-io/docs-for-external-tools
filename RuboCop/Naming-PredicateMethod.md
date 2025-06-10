Pattern: Inconsistent method name with `?`

Issue: -

## Description

Checks that predicate methods end with `?` and non-predicate methods do not.

The names of predicate methods (methods that return a boolean value) should end in a question mark. Methods that don’t return a boolean, shouldn’t end in a question mark.

The rule assesses a predicate method as one that returns boolean values. Likewise, a method that only returns literal values is assessed as non-predicate. The cop does not make an assessment if the return type is unknown (method calls, variables, etc.).

## Examples

```ruby
# bad
def foo
  bar == baz
end

# good
def foo?
  bar == baz
end

# bad
def foo?
  5
end

# good
def foo
  5
end

# good - operator method
def ==(other)
  hash == other.hash
end

# good - at least one return value is boolean
def foo?
  return unless bar?
  true
end

# ok - return type is not known
def foo?
  bar
end

# ok - return type is not known
def foo
  bar?
end
```

## Further Reading

* [RuboCop - Naming/PredicateMethod](https://docs.rubocop.org/rubocop/cops_naming.html#namingpredicatemethod)