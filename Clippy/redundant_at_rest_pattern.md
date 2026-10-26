Pattern: Redundant `[x @ ..]` pattern

Issue: -

## Description

In all cases, `all` works fine and can often make code simpler, as you possibly won't need
to convert from say a `Vec` to a slice by dereferencing.

## What it does

Checks for `[all @ ..]` patterns.

## Examples

Example of **incorrect** code:

```rust
if let [all @ ..] = &*v {
    // NOTE: Type is a slice here
    println!("all elements: {all:#?}");
}
```

Example of **correct** code:

```rust
if let all = v {
    // NOTE: Type is a `Vec` here
    println!("all elements: {all:#?}");
}
// or
println!("all elements: {v:#?}");
```

## Further Reading

* [Clippy - redundant_at_rest_pattern](https://clippy.rust-lang.org/stable/index.html#redundant_at_rest_pattern)
