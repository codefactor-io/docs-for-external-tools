Pattern: Missing use of `Enumerable` method

Issue: -

## Description

Prefer `Enumerable` predicate methods over expressions with `count`.

Querying methods express the intention more clearly and are more performant in some cases. For example, `articles.any?(&:published?)` is more readable than `articles.count(&:published?) > 0` and also more performant because `#any?` stops execution as soon as the first published article is found, while `#count` traverses the whole collection.

## Examples

```ruby
# bad
x.count.positive?
x.count > 0
x.count != 0

x.count(&:foo?).positive?
x.count { |item| item.foo? }.positive?

# good
x.any?

x.any?(&:foo?)
x.any? { |item| item.foo? }

# bad
x.count.zero?
x.count == 0

# good
x.none?

# bad
x.count == 1
x.one?
```

## Further Reading

* [RuboCop - CollectionQuerying](https://docs.rubocop.org/rubocop/cops_style.html#stylecollectionquerying)