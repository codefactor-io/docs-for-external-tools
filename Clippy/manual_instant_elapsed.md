Pattern: Missing use of `Instant::elapsed()`

Issue: -

## Description

It is easy to accidentally write `prev_instant - Instant::now()`, which will always be 0ns
as `Instant` subtraction saturates.

`prev_instant.elapsed()` also more clearly signals intention.

## What it does

Lints subtraction between `Instant::now()` and another `Instant`.

## Examples

Example of **incorrect** code:

```rust
use std::time::Instant;
let prev_instant = Instant::now();
let duration = Instant::now() - prev_instant;
```

Example of **correct** code:

```rust
use std::time::Instant;
let prev_instant = Instant::now();
let duration = prev_instant.elapsed();
```

## Further Reading

* [Clippy - manual_instant_elapsed](https://clippy.rust-lang.org/stable/index.html#manual_instant_elapsed)
