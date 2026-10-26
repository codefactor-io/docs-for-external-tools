Pattern: Missing use of `clamp()`

Issue: -

## Description

clamp is much shorter, easier to read, and doesn't use any control flow.

## What it does

Identifies good opportunities for a clamp function from std or core, and suggests using it.

## Examples

```rust
if input > max {
    max
} else if input < min {
    min
} else {
    input
}
```

```rust
input.max(min).min(max)
```

```rust
match input {
    x if x > max => max,
    x if x < min => min,
    x => x,
}
```

```rust
let mut x = input;
if x < min { x = min; }
if x > max { x = max; }
```
Use instead:
```rust
input.clamp(min, max)
```

## Limitations

This lint will only trigger if max and min are known at compile time, and max is
greater than min.

## Known issue(s)

If the clamped variable is NaN this suggestion will cause the code to propagate NaN
rather than returning either `max` or `min`.

`clamp` functions will panic if `max < min`, `max.is_nan()`, or `min.is_nan()`.
Some may consider panicking in these situations to be desirable, but it also may
introduce panicking where there wasn't any before.

See also [the discussion in the
PR](https://github.com/rust-lang/rust-clippy/pull/9484#issuecomment-1278922613).

## Further Reading

* [Clippy - manual_clamp](https://clippy.rust-lang.org/stable/index.html#manual_clamp)
