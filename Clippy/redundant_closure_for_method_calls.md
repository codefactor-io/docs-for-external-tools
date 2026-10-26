Pattern: Redundant closure for method call

Issue: -

## Description

It's unnecessary to create the closure.

## What it does

Checks for closures which only invoke a method on the closure
argument and can be replaced by referencing the method directly.

## Examples

```rust
Some('a').map(|s| s.to_uppercase());
```
may be rewritten as
```rust
Some('a').map(char::to_uppercase);
```

## Further Reading

* [Clippy - redundant_closure_for_method_calls](https://clippy.rust-lang.org/stable/index.html#redundant_closure_for_method_calls)
