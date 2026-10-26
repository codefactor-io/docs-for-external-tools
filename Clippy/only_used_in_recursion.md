Pattern: Argument only used in recursion

Issue: -

## Description

It could contain a useless calculation and can make function simpler.

The arguments can be involved in calculations and assignments but as long as
the calculations have no side-effects (function calls or mutating dereference)
and the assigned variables are also only in recursion, it is useless.

## What it does

Checks for arguments that are only used in recursion with no side-effects.

## Examples

Example of **incorrect** code:

```rust
fn f(a: usize, b: usize) -> usize {
    if a == 0 {
        1
    } else {
        f(a - 1, b + 1)
    }
}
```

Example of **correct** code:

```rust
fn f(a: usize) -> usize {
    if a == 0 {
        1
    } else {
        f(a - 1)
    }
}
```

## Known problems

Too many code paths in the linting code are currently untested and prone to produce false
positives or are prone to have performance implications.

In some cases, this would not catch all useless arguments.

```rust
fn foo(a: usize, b: usize) -> usize {
    let f = |x| x + 1;

    if a == 0 {
        1
    } else {
        foo(a - 1, f(b))
    }
}
```

For example, the argument `b` is only used in recursion, but the lint would not catch it.

List of some examples that can not be caught:
- binary operation of non-primitive types
- closure usage
- some `break` relative operations
- struct pattern binding

Also, when you recurse the function name with path segments, it is not possible to detect.

## Further Reading

* [Clippy - only_used_in_recursion](https://clippy.rust-lang.org/stable/index.html#only_used_in_recursion)
