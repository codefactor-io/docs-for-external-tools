Pattern: Block in `if` or `match` condition

Issue: -

## Description

Style, using blocks in the condition makes it hard to read.

## What it does

Checks for `if` and `match` conditions that use blocks containing an
expression, statements or conditions that use closures with blocks.

## Examples

Example of **incorrect** code:

```rust
if { true } { /* ... */ }

if { let x = somefunc(); x } { /* ... */ }

match { let e = somefunc(); e } {
    // ...
}
```

Example of **correct** code:

```rust
if true { /* ... */ }

let res = { let x = somefunc(); x };
if res { /* ... */ }

let res = { let e = somefunc(); e };
match res {
    // ...
}
```

## Further Reading

* [Clippy - blocks_in_conditions](https://clippy.rust-lang.org/stable/index.html#blocks_in_conditions)
