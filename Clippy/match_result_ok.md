Pattern: Unnecessary `ok()` in `if let` or `while let`

Issue: -

## Description

Calling `ok()` in `while let` is unnecessary, instead match
on `Ok(pat)`

## What it does

Checks for unnecessary `ok()` in `while let`.

## Examples

Example of **incorrect** code:

```rust
while let Some(value) = iter.next().ok() {
    vec.push(value)
}

if let Some(value) = iter.next().ok() {
    vec.push(value)
}
```

Example of **correct** code:

```rust
while let Ok(value) = iter.next() {
    vec.push(value)
}

if let Ok(value) = iter.next() {
       vec.push(value)
}
```

## Further Reading

* [Clippy - match_result_ok](https://clippy.rust-lang.org/stable/index.html#match_result_ok)
