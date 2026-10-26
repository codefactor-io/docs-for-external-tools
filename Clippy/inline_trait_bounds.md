Pattern: Trait bound outside `where` clause

Issue: -

## Description

Enforce a single style throughout a codebase.
Avoid uncertainty about whether a bound should be inline
or out-of-line (i.e. a where bound).
Avoid complex inline bounds, which could make a function declaration more difficult to read.

## What it does

Enforce that `where` bounds are used for all trait bounds.

## Examples

Example of **incorrect** code:

```rust
fn foo<T: Clone>() {}
```

Example of **correct** code:

```rust
fn foo<T>() where T: Clone {}
```

## Known limitations

Only lints functions and method declararions. Bounds on structs, enums,
and impl blocks are not yet covered.

## Further Reading

* [Clippy - inline_trait_bounds](https://clippy.rust-lang.org/stable/index.html#inline_trait_bounds)
