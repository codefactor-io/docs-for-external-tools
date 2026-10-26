Pattern: Useless `as_ref()` call

Issue: -

## Description

The call is unnecessary.

## What it does

Checks for usage of `.as_ref()` or `.as_mut()` where the
types before and after the call are the same.

## Examples

Example of **incorrect** code:

```rust
let x: &[i32] = &[1, 2, 3, 4, 5];
do_stuff(x.as_ref());
```

Example of **correct** code:

```rust
let x: &[i32] = &[1, 2, 3, 4, 5];
do_stuff(x);
```

## Further Reading

* [Clippy - useless_asref](https://clippy.rust-lang.org/stable/index.html#useless_asref)
