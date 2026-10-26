Pattern: Single-character string as pattern

Issue: -

## Description

While this can make a perf difference on some systems,
benchmarks have proven inconclusive. But at least using a
char literal makes it clear that we are looking at a single
character.

## What it does

Checks for string methods that receive a single-character
`str` as an argument, e.g., `_.split("x")`.

## Examples

Example of **incorrect** code:

```rust
_.split("x");
```

Example of **correct** code:

```rust
_.split('x');
```

## Known problems

Does not catch multi-byte unicode characters. This is by
design, on many machines, splitting by a non-ascii char is
actually slower. Please do your own measurements instead of
relying solely on the results of this lint.

## Further Reading

* [Clippy - single_char_pattern](https://clippy.rust-lang.org/stable/index.html#single_char_pattern)
