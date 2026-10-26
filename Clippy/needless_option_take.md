Pattern: Unnecessary `take()` after `as_ref()`

Issue: -

## Description

Redundant code. `take` writes `None` to its argument.
In this case the modification is useless as it's a temporary that cannot be read from afterwards.

## What it does

Checks for calling `take` function after `as_ref`.

## Examples

Example of **incorrect** code:

```rust
let x = Some(3);
x.as_ref().take();
```

Example of **correct** code:

```rust
let x = Some(3);
x.as_ref();
```

## Further Reading

* [Clippy - needless_option_take](https://clippy.rust-lang.org/stable/index.html#needless_option_take)
