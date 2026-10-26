Pattern: Use of `fold()` with `Try` type

Issue: -

## Description

The code should use `try_fold` instead, which short-circuits on failure, thus opening the
door for additional optimizations not possible with `fold` as rustc can guarantee the
function is never called on `None`, `Err`, etc., alleviating otherwise necessary checks. It's
also slightly more idiomatic.

## What it does

Checks for usage of `Iterator::fold` with a type that implements `Try`.

## Examples

Example of **incorrect** code:

```rust
vec![1, 2, 3].iter().fold(Some(0i32), |sum, i| sum?.checked_add(*i));
```

Example of **correct** code:

```rust
vec![1, 2, 3].iter().try_fold(0i32, |sum, i| sum.checked_add(*i));
```

## Known issues

This lint doesn't take into account whether a function does something on the failure case,
i.e., whether short-circuiting will affect behavior. Refactoring to `try_fold` is not
desirable in those cases.

## Further Reading

* [Clippy - manual_try_fold](https://clippy.rust-lang.org/stable/index.html#manual_try_fold)
