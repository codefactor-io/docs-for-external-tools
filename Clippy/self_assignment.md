Pattern: Self-assignment

Issue: -

## Description

Self-assignments are redundant and unlikely to be
intentional.

## What it does

Checks for explicit self-assignments.

## Examples

Example of **incorrect** code:

```rust
struct Event {
    x: i32,
}

fn copy_position(a: &mut Event, b: &Event) {
    a.x = a.x;
}
```

Example of **correct** code:

```rust
struct Event {
    x: i32,
}

fn copy_position(a: &mut Event, b: &Event) {
    a.x = b.x;
}
```

## Known problems

If expression contains any deref coercions or
indexing operations they are assumed not to have any side effects.

## Further Reading

* [Clippy - self_assignment](https://clippy.rust-lang.org/stable/index.html#self_assignment)
