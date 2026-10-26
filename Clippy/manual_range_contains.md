Pattern: Missing use of range `contains()`

Issue: -

## Description

`contains` expresses the intent better and has less
failure modes (such as fencepost errors or using `||` instead of `&&`).

## What it does

Checks for expressions like `x >= 3 && x < 8` that could
be more readably expressed as `(3..8).contains(&x)`.

## Examples

Example of **incorrect** code:

```rust
// given
let x = 6;

assert!(x >= 3 && x < 8);
```

Example of **correct** code:

```rust
assert!((3..8).contains(&x));
```

## Limitations

Out-of-range checks on floating-point types, such as `q < 0.0 || q > 1.0`,
are not linted. For `NaN`, that expression is `false`, but
`!(0.0..=1.0).contains(&q)` is `true`, so the suggested rewrite would
change control flow.

## Further Reading

* [Clippy - manual_range_contains](https://clippy.rust-lang.org/stable/index.html#manual_range_contains)
