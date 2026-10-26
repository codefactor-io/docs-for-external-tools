Pattern: Suboptimal unit in `Duration` constructor

Issue: -

## Description

Using a smaller unit for a duration that is evenly divisible by a larger unit reduces
readability. Readers have to mentally convert values, which can be error-prone and makes
the code less clear.

## What it does

Checks for instances where a `std::time::Duration` is constructed using a smaller time unit
when the value could be expressed more clearly using a larger unit.

For literal values that would convert to 10 or fewer of the larger unit,
this lint does not apply.

## Examples

Example of **incorrect** code:

```rust
use std::time::Duration;

let dur = Duration::from_millis(50_000);
let dur = Duration::from_secs(1800);
let dur = Duration::from_mins(10 * 60);
```

Example of **correct** code:

```rust
use std::time::Duration;

let dur = Duration::from_secs(50);
let dur = Duration::from_mins(30);
let dur = Duration::from_hours(10);
```

## Further Reading

* [Clippy - duration_suboptimal_units](https://clippy.rust-lang.org/stable/index.html#duration_suboptimal_units)
