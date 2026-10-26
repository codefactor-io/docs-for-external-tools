Pattern: Similar binding names

Issue: -

## Description

It's hard to distinguish between names that differ only
by a single character.

## What it does

Checks for names that are very similar and thus confusing. In particular,
the lint checks for names with a single character change.

It does not warn about names that have a single additional character at
the beginning nor the end; only insertions in the middle are considered.

Note: this lint looks for similar names throughout each
scope. To allow it, you need to allow it on the scope
level, not on the name that is reported.

## Examples

```rust
let checked_exp = something;
let checked_eap = something_else;
```

```rust
let orange = val;
let ornange = val2;
```

## Further Reading

* [Clippy - similar_names](https://clippy.rust-lang.org/stable/index.html#similar_names)
