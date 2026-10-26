Pattern: Suspicious grouping of binary operations

Issue: -

## Description

They are probably bugs and if they aren't then they look like bugs
and you should add a comment explaining why you are doing such an
odd set of operations.

## What it does

Checks for unlikely usages of binary operators that are almost
certainly typos and/or copy/paste errors, given the other usages
of binary operators nearby.

## Examples

Example of **incorrect** code:

```rust
struct Vec3 {
    x: f64,
    y: f64,
    z: f64,
}

impl Eq for Vec3 {}

impl PartialEq for Vec3 {
    fn eq(&self, other: &Self) -> bool {
        // This should trigger the lint because `self.x` is compared to `other.y`
        self.x == other.y && self.y == other.y && self.z == other.z
    }
}
```

Example of **correct** code:

```rust
// same as above except:
impl PartialEq for Vec3 {
    fn eq(&self, other: &Self) -> bool {
        // Note we now compare other.x to self.x
        self.x == other.x && self.y == other.y && self.z == other.z
    }
}
```

## Known problems

There may be some false positives if you are trying to do something
unusual that happens to look like a typo.

## Further Reading

* [Clippy - suspicious_operation_groupings](https://clippy.rust-lang.org/stable/index.html#suspicious_operation_groupings)
