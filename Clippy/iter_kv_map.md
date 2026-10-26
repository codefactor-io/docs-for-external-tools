Pattern: Map iteration ignoring keys or values

Issue: -

## Description

Readability. There are `keys` and `values` methods that
can be used to express that we only need the keys or the values.

## What it does

Checks for iterating a map (`HashMap` or `BTreeMap`) and
ignoring either the keys or values.

## Examples

Example of **incorrect** code:

```rust
let map: HashMap<u32, u32> = HashMap::new();
let values = map.iter().map(|(_, value)| value).collect::<Vec<_>>();
```

Example of **correct** code:

```rust
let map: HashMap<u32, u32> = HashMap::new();
let values = map.values().collect::<Vec<_>>();
```

## Further Reading

* [Clippy - iter_kv_map](https://clippy.rust-lang.org/stable/index.html#iter_kv_map)
