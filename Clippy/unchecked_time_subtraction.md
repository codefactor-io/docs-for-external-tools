Pattern: Unchecked `Duration` or `Instant` subtraction

Issue: -

## Description

Unchecked subtraction could cause underflow on certain platforms, leading to
unintentional panics.

## What it does

Lints subtraction between an `Instant` and a `Duration`, or between two `Duration` values.

## Examples

Example of **incorrect** code:

```rust
let time_passed = Instant::now() - Duration::from_secs(5);
let dur1 = Duration::from_secs(3);
let dur2 = Duration::from_secs(5);
let diff = dur1 - dur2;
```

Example of **correct** code:

```rust
let time_passed = Instant::now().checked_sub(Duration::from_secs(5));
let dur1 = Duration::from_secs(3);
let dur2 = Duration::from_secs(5);
let diff = dur1.checked_sub(dur2);
```

## Further Reading

* [Clippy - unchecked_time_subtraction](https://clippy.rust-lang.org/stable/index.html#unchecked_time_subtraction)
