Pattern: Hashing of unit value

Issue: -

## Description

Hashing a unit value doesn't do anything as the implementation of `Hash` for `()` is a no-op.

## What it does

Detects `().hash(_)`.

## Examples

Example of **incorrect** code:

```rust
match my_enum {
	Empty => ().hash(&mut state),
	WithValue(x) => x.hash(&mut state),
}
```

Example of **correct** code:

```rust
match my_enum {
	Empty => 0_u8.hash(&mut state),
	WithValue(x) => x.hash(&mut state),
}
```

## Further Reading

* [Clippy - unit_hash](https://clippy.rust-lang.org/stable/index.html#unit_hash)
