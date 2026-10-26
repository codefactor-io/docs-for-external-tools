Pattern: Missing use of `Duration::subsec_*` method

Issue: -

## Description

It's more concise to call `Duration::subsec_micros()` or
`Duration::subsec_millis()` than to calculate them.

## What it does

Checks for calculation of subsecond microseconds or milliseconds
from other `Duration` methods.

## Examples

Example of **incorrect** code:

```rust
let micros = duration.subsec_nanos() / 1_000;
let millis = duration.subsec_nanos() / 1_000_000;
```

Example of **correct** code:

```rust
let micros = duration.subsec_micros();
let millis = duration.subsec_millis();
```

## Further Reading

* [Clippy - duration_subsec](https://clippy.rust-lang.org/stable/index.html#duration_subsec)
