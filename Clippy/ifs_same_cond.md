Pattern: Identical `if` conditions

Issue: -

## Description

This is probably a copy & paste error.

## What it does

Checks for consecutive `if`s with the same condition.

## Examples

```rust
if a == b {
    …
} else if a == b {
    …
}
```

Note that this lint ignores all conditions with a function call as it could
have side effects:

```rust
if foo() {
    …
} else if foo() { // not linted
    …
}
```

## Further Reading

* [Clippy - ifs_same_cond](https://clippy.rust-lang.org/stable/index.html#ifs_same_cond)
