Pattern: Missing use of `keys()` or `values()`

Issue: -

## Description

Readability. There are `keys` and `values` methods that
can be used to express that don't need the values or keys.

## What it does

Checks for iterating a map (`HashMap` or `BTreeMap`) and
ignoring either the keys or values.

## Examples

Example of **incorrect** code:

```rust
for (k, _) in &map {
    ..
}
```

Example of **correct** code:

```rust
for k in map.keys() {
    ..
}
```

## Further Reading

* [Clippy - for_kv_map](https://clippy.rust-lang.org/stable/index.html#for_kv_map)
