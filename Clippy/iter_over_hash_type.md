Pattern: Iteration over hash-based collection

Issue: -

## Description

Because hash types are unordered, when iterated through such as in a `for` loop, the values are returned in
an undefined order. As a result, on redundant systems this may cause inconsistencies and anomalies.
In addition, the unknown order of the elements may reduce readability or introduce other undesired
side effects.

## What it does

This is a restriction lint which prevents the use of hash types (i.e., `HashSet` and `HashMap`) in for loops.

## Examples

Example of **incorrect** code:

```rust
    let my_map = std::collections::HashMap::<i32, String>::new();
    for (key, value) in my_map { /* ... */ }
```

Example of **correct** code:

```rust
    let my_map = std::collections::HashMap::<i32, String>::new();
    let mut keys = my_map.keys().clone().collect::<Vec<_>>();
    keys.sort();
    for key in keys {
        let value = &my_map[key];
    }
```

## Further Reading

* [Clippy - iter_over_hash_type](https://clippy.rust-lang.org/stable/index.html#iter_over_hash_type)
