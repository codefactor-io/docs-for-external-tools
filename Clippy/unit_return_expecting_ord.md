Pattern: Closure returning unit instead of `Ord`

Issue: -

## Description

Likely, returning the unit type is unintentional, and
could simply be caused by an extra semi-colon. Since () implements Ord
it doesn't cause a compilation error.
This is the same reasoning behind the unit_cmp lint.

## What it does

Checks for functions that expect closures of type
Fn(...) -> Ord where the implemented closure returns the unit type.
The lint also suggests to remove the semi-colon at the end of the statement if present.

## Examples

Example of **incorrect** code:

```rust
let mut twins = vec![(1, 1), (2, 2)];
twins.sort_by_key(|x| { x.1; });
```

## Known problems

If returning unit is intentional, then there is no
way of specifying this without triggering needless_return lint

## Further Reading

* [Clippy - unit_return_expecting_ord](https://clippy.rust-lang.org/stable/index.html#unit_return_expecting_ord)
