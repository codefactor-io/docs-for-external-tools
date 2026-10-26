Pattern: Use of `#[cfg(not(test))]`

Issue: -

## Description

This may give the false impression that a codebase has 100% coverage, yet actually has untested code.
Enabling this also guards against excessive mockery as well, which is an anti-pattern.

## What it does

Checks for usage of `cfg` that excludes code from `test` builds. (i.e., `#[cfg(not(test))]`)

## Examples

Example of **incorrect** code:

```rust
#[cfg(not(test))]
important_check(); // I'm not actually tested, but not including me will falsely increase coverage!
```

Example of **correct** code:

```rust
important_check();
```

## Further Reading

* [Clippy - cfg_not_test](https://clippy.rust-lang.org/stable/index.html#cfg_not_test)
