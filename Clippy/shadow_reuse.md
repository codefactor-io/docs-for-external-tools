Pattern: Shadowed binding reusing original value

Issue: -

## Description

Some argue that name shadowing like this hurts readability,
because a value may be bound to different things depending on position in
the code.

See also `shadow_same` and `shadow_unrelated` for other restrictions on shadowing.

## What it does

Checks for bindings that shadow other bindings already in
scope, while reusing the original value.

## Examples

```rust
let x = 2;
let x = x + 1;
```
use different variable name:
```rust
let x = 2;
let y = x + 1;
```

## Further Reading

* [Clippy - shadow_reuse](https://clippy.rust-lang.org/stable/index.html#shadow_reuse)
