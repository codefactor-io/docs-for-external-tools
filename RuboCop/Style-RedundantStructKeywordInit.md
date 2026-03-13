Pattern: Redundant `keyword_init` for `Struct.new`

Issue: -

## Description

Checks for redundant `keyword_init` option for `Struct.new`.

Since Ruby 3.2, `keyword_init` in `Struct.new` defaults to `nil` behavior. Therefore, this cop detects and autocorrects redundant `keyword_init: nil` and `keyword_init: true` in `Struct.new`.

## Examples

```
# bad
Struct.new(:foo, keyword_init: nil)
Struct.new(:foo, keyword_init: true)

# good
Struct.new(:foo)
```

## Further Reading

* [RuboCop - Style/RedundantStructKeywordInit](https://docs.rubocop.org/rubocop/latest/cops_style.html#styleredundantstructkeywordinit)
