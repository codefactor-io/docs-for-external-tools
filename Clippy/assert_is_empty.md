Pattern: `assert!` on `is_empty()` hiding the value

Issue: -

## Description

A boolean assertion only reports that the emptiness check failed. It does not show what the
asserted value contained.

In CI or another remote test service, the failure output tells you that the value was
unexpectedly empty or non-empty, but not which values were present. The next step is often
to reproduce the failure locally, add temporary logging, or change the test so it exposes
the value. That extra investigation can be much slower than fixing the problem from the
original CI failure.

The emptiness check also commonly appears before a deeper contents assertion:

```rust
assert!(!items.is_empty());
assert_eq!(items[0], "bar");
```

If the first assertion fails, the second assertion never runs, so the failure can hide the
check that would have shown more useful context.

Instead, compare the value with an empty value using `assert_eq!`, `assert_ne!`,
`debug_assert_eq!`, or `debug_assert_ne!`. These macros print the asserted value on failure.

## What it does

Checks assertions that only test whether a supported value is empty.

The lint handles `assert!` and `debug_assert!` calls on strings, slices, arrays, and `Vec`.

## Examples

Example of **incorrect** code:

```rust
assert!(items.is_empty());
assert!(!items.is_empty());
```

Example of **correct** code:

```rust
assert_eq!(items, [] as [i32; 0]);
assert_ne!(items, [] as [i32; 0]);
```

## Known problems

Printing the asserted value can be undesirable outside tests, especially when the value may
be very large or contain sensitive information. If the assertion failure should not reveal
the value, keep the boolean assertion and allow this lint at that assertion.

## Further Reading

* [Clippy - assert_is_empty](https://clippy.rust-lang.org/stable/index.html#assert_is_empty)
