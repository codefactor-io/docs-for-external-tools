Pattern: Use of item newer than MSRV

Issue: -

## Description

It would prevent the crate to be actually used with the specified MSRV.

## What it does

This lint checks that no function newer than the defined MSRV (minimum
supported rust version) is used in the crate.

## Examples

```rust
// MSRV of 1.3.0
use std::thread::sleep;
use std::time::Duration;

// Sleep was defined in `1.4.0`.
sleep(Duration::new(1, 0));
```

To fix this problem, either increase your MSRV or use another item
available in your current MSRV.

You can also locally change the MSRV that should be checked by Clippy,
for example if a feature in your crate (e.g., `modern_compiler`) should
allow you to use an item:

```rust
//! This crate has a MSRV of 1.3.0, but we also have an optional feature
//! `sleep_well` which requires at least Rust 1.4.0.

// When the `sleep_well` feature is set, do not warn for functions available
// in Rust 1.4.0 and below.
#![cfg_attr(feature = "sleep_well", clippy::msrv = "1.4.0")]

use std::time::Duration;

#[cfg(feature = "sleep_well")]
fn sleep_for_some_time() {
    std::thread::sleep(Duration::new(1, 0)); // Will not trigger the lint
}
```

You can also increase the MSRV in tests, by using:

```rust
// Use a much higher MSRV for tests while keeping the main one low
#![cfg_attr(test, clippy::msrv = "1.85.0")]

#[test]
fn my_test() {
    // The tests can use items introduced in Rust 1.85.0 and lower
    // without triggering the `incompatible_msrv` lint.
}
```

## Further Reading

* [Clippy - incompatible_msrv](https://clippy.rust-lang.org/stable/index.html#incompatible_msrv)
