Pattern: Use of identity `map()`

Issue: -

## Description

It can be written more concisely without the call to `map`.

## What it does

Checks for instances of `map(f)` where `f` is the identity function.

## Examples

Example of **incorrect** code:

```rust
let x = [1, 2, 3];
let y: Vec<_> = x.iter().map(|x| x).map(|x| 2*x).collect();
```

Example of **correct** code:

```rust
let x = [1, 2, 3];
let y: Vec<_> = x.iter().map(|x| 2*x).collect();
```

## Further Reading

* [Clippy - map_identity](https://clippy.rust-lang.org/stable/index.html#map_identity)
