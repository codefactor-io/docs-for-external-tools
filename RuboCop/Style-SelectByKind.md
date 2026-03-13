Pattern: Select by kind

Issue: -

## Description

Looks for places where a subset of an `Enumerable (array, range, set, etc.; see note below)` is calculated based on a class type check, and suggests `grep` or `grep_v` instead.

## Examples

```
# bad (select or find_all)
array.select { |x| x.is_a?(Foo) }
array.select { |x| x.kind_of?(Foo) }

# bad (reject)
array.reject { |x| x.is_a?(Foo) }

# bad (negative form)
array.reject { |x| !x.is_a?(Foo) }

# good
array.grep(Foo)
array.grep_v(Foo)
```

## Further Reading

* [RuboCop - Style/SelectByKind](https://docs.rubocop.org/rubocop/latest/cops_style.html#styleselectbykind)
