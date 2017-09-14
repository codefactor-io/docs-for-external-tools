Pattern: Naming/PredicateName

Issue: -

## Description

This cop makes sure that predicates are named properly.

### Example

```ruby
# bad
def is_even?(value) ...

# good
def even?(value)

# bad
def has_value? ...

# good
def value? ...
```

## Default configuration

Attribute | Value
--- | ---
NamePrefix | is_, has_, have_
NamePrefixBlacklist | is_, has_, have_
NameWhitelist | is_a?
Exclude | spec/\*\*/\*

## Further Reading

* [RuboCop - Naming/PredicateName](https://rubocop.readthedocs.io/en/latest/cops_naming/#namingpredicatename)
* [https://github.com/bbatsov/ruby-style-guide#bool-methods-qmark](https://github.com/bbatsov/ruby-style-guide#bool-methods-qmark)