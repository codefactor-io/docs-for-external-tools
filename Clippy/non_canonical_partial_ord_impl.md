Pattern: Non-canonical `PartialOrd` implementation

Issue: -

## Description

If both `PartialOrd` and `Ord` are implemented, they must agree. This is commonly done by
wrapping the result of `cmp` in `Some` for `partial_cmp`. Not doing this may silently
introduce an error upon refactoring.

## What it does

Checks for non-canonical implementations of `PartialOrd` when `Ord` is already implemented.

## Examples

Example of **incorrect** code:

```rust
#[derive(Eq, PartialEq)]
struct A(u32);

impl Ord for A {
    fn cmp(&self, other: &Self) -> Ordering {
        // ...
    }
}

impl PartialOrd for A {
    fn partial_cmp(&self, other: &Self) -> Option<Ordering> {
        // ...
    }
}
```

Example of **correct** code:

```rust
#[derive(Eq, PartialEq)]
struct A(u32);

impl Ord for A {
    fn cmp(&self, other: &Self) -> Ordering {
        // ...
    }
}

impl PartialOrd for A {
    fn partial_cmp(&self, other: &Self) -> Option<Ordering> {
        Some(self.cmp(other))   // or self.cmp(other).into()
    }
}
```

## Known issues

Code that calls the `.into()` method instead will be flagged, despite `.into()` wrapping it
in `Some`.

## Further Reading

* [Clippy - non_canonical_partial_ord_impl](https://clippy.rust-lang.org/stable/index.html#non_canonical_partial_ord_impl)
