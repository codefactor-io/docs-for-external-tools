Pattern: Use of `unwrap_or()` with default value

Issue: -

## Description

Readability. Using `unwrap_or_default` in place of `unwrap_or`/`unwrap_or_else`, or `or_default`
in place of `or_insert`/`or_insert_with`, is simpler and more concise.

## What it does

Checks for usages of the following functions with an argument that constructs a default value
(e.g., `Default::default` or `String::new`):
- `unwrap_or`
- `unwrap_or_else`
- `or_insert`
- `or_insert_with`

## Examples

Example of **incorrect** code:

```rust
x.unwrap_or(Default::default());
map.entry(42).or_insert_with(String::new);
```

Example of **correct** code:

```rust
x.unwrap_or_default();
map.entry(42).or_default();
```

## Known problems

In some cases, the argument of `unwrap_or`, etc. is needed for type inference. The lint uses a
heuristic to try to identify such cases. However, the heuristic can produce false negatives.

## Further Reading

* [Clippy - unwrap_or_default](https://clippy.rust-lang.org/stable/index.html#unwrap_or_default)
