Pattern: Unnecessary `NonZero::get()`

Issue: -

## Description

The `get` call adds nothing but noise, as the method could be called on the
`NonZero` value directly.

## What it does

Checks for `NonZero::get` calls that are immediately followed by a method or operator
which `NonZero` provides itself, with the same return type.

## Examples

```rust
let _ = nz.get().leading_zeros();
```
Use instead:
```rust
let _ = nz.leading_zeros();
```

The lint also handles division and remainder operators:
```rust
let _ = 4 / nz.get();
```
Use instead:
```rust
let _ = 4 / nz;
```

## Further Reading

* [Clippy - needless_nonzero_get](https://clippy.rust-lang.org/stable/index.html#needless_nonzero_get)
