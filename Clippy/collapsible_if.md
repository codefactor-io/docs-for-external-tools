Pattern: Collapsible nested `if`

Issue: -

## Description

Each `if`-statement adds one level of nesting, which
makes code look more complex than it really is.

## What it does

Checks for nested `if` statements which can be collapsed
by `&&`-combining their conditions.

## Examples

Example of **incorrect** code:

```rust
if x {
    if y {
        // …
    }
}
```

Example of **correct** code:

```rust
if x && y {
    // …
}
```

## Further Reading

* [Clippy - collapsible_if](https://clippy.rust-lang.org/stable/index.html#collapsible_if)
