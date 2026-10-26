Pattern: Redundant closure

Issue: -

## Description

Needlessly creating a closure adds code for no benefit
and gives the optimizer more work.

## What it does

Checks for closures which just call another function where
the function can be called directly. `unsafe` functions, calls where types
get adjusted or where the callee is marked `#[track_caller]` are ignored.

## Examples

Example of **incorrect** code:

```rust
xs.map(|x| foo(x))
```

Example of **correct** code:

```rust
// where `foo(_)` is a plain function that takes the exact argument type of `x`.
xs.map(foo)
```

## Further Reading

* [Clippy - redundant_closure](https://clippy.rust-lang.org/stable/index.html#redundant_closure)
