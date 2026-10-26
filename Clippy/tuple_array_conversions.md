Pattern: Manual tuple and array conversion

Issue: -

## Description

It may be unnecessary complexity. `.into()` works for converting tuples<=> arrays of up to
12 elements and conveys the intent more clearly, while also leaving less room for hard to
spot bugs!

## What it does

Checks for tuple<=>array conversions that are not done with `.into()`.

## Examples

Example of **incorrect** code:

```rust
let t1 = &[(1, 2), (3, 4)];
let v1: Vec<[u32; 2]> = t1.iter().map(|&(a, b)| [a, b]).collect();
```

Example of **correct** code:

```rust
let t1 = &[(1, 2), (3, 4)];
let v1: Vec<[u32; 2]> = t1.iter().map(|&t| t.into()).collect();
```

## Known issues

The suggested code may hide potential asymmetry in some cases. See
[#11085](https://github.com/rust-lang/rust-clippy/issues/11085) for more info.

## Further Reading

* [Clippy - tuple_array_conversions](https://clippy.rust-lang.org/stable/index.html#tuple_array_conversions)
