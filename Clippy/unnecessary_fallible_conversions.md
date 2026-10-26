Pattern: Unnecessary fallible conversion

Issue: -

## Description

In those cases, the `TryInto` and `TryFrom` trait implementation is a blanket impl that forwards
to `Into` or `From`, which always succeeds.
The returned `Result<_, Infallible>` requires error handling to get the contained value
even though the conversion can never fail.

## What it does

Checks for calls to `TryInto::try_into` and `TryFrom::try_from` when their infallible counterparts
could be used.

## Examples

```rust
let _: Result<i64, _> = 1i32.try_into();
let _: Result<i64, _> = <_>::try_from(1i32);
```
Use `from`/`into` instead:
```rust
let _: i64 = 1i32.into();
let _: i64 = <_>::from(1i32);
```

## Further Reading

* [Clippy - unnecessary_fallible_conversions](https://clippy.rust-lang.org/stable/index.html#unnecessary_fallible_conversions)
