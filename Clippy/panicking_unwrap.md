Pattern: `unwrap()` that always fails

Issue: -

## Description

If panicking is desired, an explicit `panic!()` should be used.

## What it does

Checks for calls of `unwrap[_err]()` that will always fail.

## Examples

```rust
if option.is_none() {
    do_something_with(option.unwrap())
}
```

This code will always panic. The if condition should probably be inverted.

## Known problems

This lint only checks `if` conditions not assignments.
So something like `let x: Option<()> = None; x.unwrap();` will not be recognized.

## Further Reading

* [Clippy - panicking_unwrap](https://clippy.rust-lang.org/stable/index.html#panicking_unwrap)
