Pattern: Use of `get()` to check key presence

Issue: -

## Description

It can be done in one call with `.contains()`/`.contains_key()`.

## What it does

Checks the usage of `.get().is_some()` or `.get().is_none()` on std map types.

## Examples

Example of **incorrect** code:

```rust
let s: HashSet<String> = HashSet::new();
if s.get("a").is_some() {
    // code
}
```

Example of **correct** code:

```rust
let s: HashSet<String> = HashSet::new();
if s.contains("a") {
    // code
}
```

## Further Reading

* [Clippy - unnecessary_get_then_check](https://clippy.rust-lang.org/stable/index.html#unnecessary_get_then_check)
