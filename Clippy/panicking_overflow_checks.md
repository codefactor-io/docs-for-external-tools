Pattern: Panicking overflow check

Issue: -

## Description

These checks will, by default, panic in debug builds rather than check
whether the operation caused an overflow.

## What it does

Detects C-style underflow/overflow checks.

## Examples

```rust
if a + b < a {
    // handle overflow
}
```

Use instead:
```rust
if a.checked_add(b).is_none() {
    // handle overflow
}
```

Or:
```rust
if a.overflowing_add(b).1 {
    // handle overflow
}
```

## Further Reading

* [Clippy - panicking_overflow_checks](https://clippy.rust-lang.org/stable/index.html#panicking_overflow_checks)
