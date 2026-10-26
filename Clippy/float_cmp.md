Pattern: Use of `==` or `!=` on floats

Issue: -

## Description

Floating point calculations are usually imprecise, so asking if two values are *exactly*
equal is asking for trouble because arriving at the same logical result via different
routes (e.g. calculation versus constant) may yield different values.

## What it does

Checks for (in-)equality comparisons on floating-point
values (apart from zero), except in functions called `*eq*` (which probably
implement equality for a type involving floats).

## Examples

```rust
let a: f64 = 1000.1;
let b: f64 = 0.2;
let x = a + b;
let y = 1000.3; // Expected value.

// Actual value: 1000.3000000000001
println!("{x}");

let are_equal = x == y;
println!("{are_equal}"); // false
```

The correct way to compare floating point numbers is to define an allowed error margin. This
may be challenging if there is no "natural" error margin to permit. Broadly speaking, there
are two cases:

1. If your values are in a known range and you can define a threshold for "close enough to
   be equal", it may be appropriate to define an absolute error margin. For example, if your
   data is "length of vehicle in centimeters", you may consider 0.1 cm to be "close enough".
1. If your code is more general and you do not know the range of values, you should use a
   relative error margin, accepting e.g. 0.1% of error regardless of specific values.

For the scenario where you can define a meaningful absolute error margin, consider using:

```rust
let a: f64 = 1000.1;
let b: f64 = 0.2;
let x = a + b;
let y = 1000.3; // Expected value.

const ALLOWED_ERROR_VEHICLE_LENGTH_CM: f64 = 0.1;
let within_tolerance = (x - y).abs() < ALLOWED_ERROR_VEHICLE_LENGTH_CM;
println!("{within_tolerance}"); // true
```

NOTE: Do not use `f64::EPSILON` - while the error margin is often called "epsilon", this is
a different use of the term that is not suitable for floating point equality comparison.
Indeed, for the example above using `f64::EPSILON` as the allowed error would return `false`.

For the scenario where no meaningful absolute error can be defined, refer to
[the floating point guide](https://www.floating-point-gui.de/errors/comparison)
for a reference implementation of relative error based comparison of floating point values.
`MIN_NORMAL` in the reference implementation is equivalent to `MIN_POSITIVE` in Rust.

## Further Reading

* [Clippy - float_cmp](https://clippy.rust-lang.org/stable/index.html#float_cmp)
