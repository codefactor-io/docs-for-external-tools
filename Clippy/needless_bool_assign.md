Pattern: Unnecessary `if` assigning boolean literals

Issue: -

## Description

Redundant code.

## What it does

Checks for expressions of the form `if c { x = true } else { x = false }`
(or vice versa) and suggest assigning the variable directly from the
condition.

## Examples

Example of **incorrect** code:

```rust
if must_keep(x, y) {
    skip = false;
} else {
    skip = true;
}
```

Example of **correct** code:

```rust
skip = !must_keep(x, y);
```

## Further Reading

* [Clippy - needless_bool_assign](https://clippy.rust-lang.org/stable/index.html#needless_bool_assign)
