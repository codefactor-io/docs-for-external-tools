Pattern: Forbidden predicate method prefix

Issue: -

## Description

Checks that predicate method names end with a question mark and do not start with a forbidden prefix.

A method is determined to be a predicate method if its name starts with one of the prefixes listed in the `NamePrefix` configuration. The list defaults to `is_`, `has_`, and `have_` but may be overridden.

Predicate methods must end with a question mark.


## Examples

### NamePrefix: ['is_', 'has_', 'have_'] (default)

```ruby
# bad
def is_even(value)
end

# When ForbiddenPrefixes: ['is_', 'has_', 'have_'] (default)
# good
def even?(value)
end

# When ForbiddenPrefixes: []
# good
def is_even?(value)
end
```

## Further Reading

* [RuboCop - Naming/PredicatePrefix](https://docs.rubocop.org/rubocop/cops_naming.html#namingpredicateprefix)