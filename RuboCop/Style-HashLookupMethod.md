Pattern: Inconsistent hash lookup method

Issue: -

## Description

Enforces the use of either `Hash#[]` or `Hash#fetch` for hash lookup.

This cop can be configured to prefer either bracket-style (`[]`) or fetch-style lookup. It is disabled by default.

When enforcing `fetch` style, only single-argument bracket access is flagged. When enforcing `brackets` style, only `fetch` calls with a single key argument are flagged (not those with default values or blocks).

`Hash#[]` and `Hash#fetch` have different semantics. `Hash#[]` returns `nil` for missing keys, while `Hash#fetch` raises a `KeyError`. Replacing one with the other can change program behavior in cases where the key is missing.

## Examples

### EnforcedStyle: brackets (default)

```ruby
# bad
hash.fetch(key)

# good
hash[key]

# good - fetch with default value is allowed
hash.fetch(key, default)

# good - fetch with block is allowed
hash.fetch(key) { default }

# good - `ENV.fetch` is left to `Style/FetchEnvVar` when it is enabled
ENV.fetch(key)
```

### EnforcedStyle: fetch

```ruby
# bad
hash[key]

# good
hash.fetch(key)
```

### AllowedReceivers: ['Rails.cache']

```ruby
# good
Rails.cache.fetch(name, options) { block }
```

## Further Reading

* [RuboCop - Style/HashLookupMethod](https://docs.rubocop.org/rubocop/latest/cops_style.html#stylehashlookupmethod)
