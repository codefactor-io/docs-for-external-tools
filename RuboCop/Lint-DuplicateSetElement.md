Pattern: Duplicate set element

Issue: -

## Description

Checks for duplicate literal, constant, or variable elements in `Set` and `SortedSet`.

## Examples

```ruby
# bad
Set[:foo, :bar, :foo]

# good
Set[:foo, :bar]

# bad
Set.new([:foo, :bar, :foo])

# good
Set.new([:foo, :bar])

# bad
[:foo, :bar, :foo].to_set

# good
[:foo, :bar].to_set

# bad
SortedSet[:foo, :bar, :foo]

# good
SortedSet[:foo, :bar]

# bad
SortedSet.new([:foo, :bar, :foo])

# good
SortedSet.new([:foo, :bar])
```

## Further Reading

* [RuboCop - Lint/DuplicateSetElement](https://docs.rubocop.org/rubocop/cops_lint.html#lintduplicatesetelement)
