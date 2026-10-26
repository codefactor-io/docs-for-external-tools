Pattern: Unnecessary lazy evaluation

Issue: -

## Description

Using eager evaluation is shorter and simpler in some cases.

## What it does

As the counterpart to `or_fun_call`, this lint looks for unnecessary
lazily evaluated closures on `Option` and `Result`.

This lint suggests changing the following functions, when eager evaluation results in
simpler code:
 - `unwrap_or_else` to `unwrap_or`
 - `and_then` to `and`
 - `or_else` to `or`
 - `get_or_insert_with` to `get_or_insert`
 - `ok_or_else` to `ok_or`
 - `then` to `then_some` (for msrv >= 1.62.0)

## Examples

Example of **incorrect** code:

```rust
let opt: Option<u32> = None;

opt.unwrap_or_else(|| 42);
```

Example of **correct** code:

```rust
let opt: Option<u32> = None;

opt.unwrap_or(42);
```

## Known problems

It is possible, but not recommended for `Deref` and `Index` to have
side effects. Eagerly evaluating them can change the semantics of the program.

## Further Reading

* [Clippy - unnecessary_lazy_evaluations](https://clippy.rust-lang.org/stable/index.html#unnecessary_lazy_evaluations)
