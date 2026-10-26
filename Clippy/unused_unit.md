Pattern: Unnecessary unit expression

Issue: -

## Description

Such expressions add no value, but can make the code
less readable. Depending on formatting they can make a `break` or `return`
statement look like a function call.

## What it does

Checks for unit (`()`) expressions that can be removed.

## Examples

```rust
fn return_unit() -> () {
    ()
}
```
is equivalent to
```rust
fn return_unit() {}
```

## Further Reading

* [Clippy - unused_unit](https://clippy.rust-lang.org/stable/index.html#unused_unit)
