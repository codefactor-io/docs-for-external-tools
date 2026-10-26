Pattern: Use of `todo!`

Issue: -

## Description

The `todo!` macro indicates the presence of unfinished code,
so it should not be present in production code.

## What it does

Checks for usage of `todo!`.

## Examples

```rust
todo!();
```
Finish the implementation, or consider marking it as explicitly unimplemented.
```rust
unimplemented!();
```

## Further Reading

* [Clippy - todo](https://clippy.rust-lang.org/stable/index.html#todo)
