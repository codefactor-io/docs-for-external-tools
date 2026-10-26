Pattern: Missing use of map `entry()` API

Issue: -

## Description

Using `entry` is more efficient.

## What it does

Checks for usage of `contains_key` + `insert` on `HashMap`
or `BTreeMap`.

## Examples

Example of **incorrect** code:

```rust
if !map.contains_key(&k) {
    map.insert(k, v);
}
```

Example of **correct** code:

```rust
map.entry(k).or_insert(v);
```

## Known problems

The suggestion may have type inference errors in some cases. e.g.
```rust
let mut map = std::collections::HashMap::new();
let _ = if !map.contains_key(&0) {
    map.insert(0, 0)
} else {
    None
};
```

## Further Reading

* [Clippy - map_entry](https://clippy.rust-lang.org/stable/index.html#map_entry)
