Pattern: `map()` followed by identity `all()`/`any()`

Issue: -

## Description

The `.all(…)` or `.any(…)` methods can be called directly in place of `.map(…)`.

## What it does

Checks for usage of `.map(…)`, followed by `.all(identity)` or `.any(identity)`.

## Examples

Example of **incorrect** code:

```rust
let e1 = v.iter().map(|s| s.is_empty()).all(|a| a);
let e2 = v.iter().map(|s| s.is_empty()).any(std::convert::identity);
```

Example of **correct** code:

```rust
let e1 = v.iter().all(|s| s.is_empty());
let e2 = v.iter().any(|s| s.is_empty());
```

## Further Reading

* [Clippy - map_all_any_identity](https://clippy.rust-lang.org/stable/index.html#map_all_any_identity)
