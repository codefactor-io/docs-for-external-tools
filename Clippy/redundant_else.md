Pattern: Redundant `else` block

Issue: -

## Description

The `else` block adds unnecessary indentation and verbosity.

## What it does

Checks for `else` blocks that can be removed without changing semantics.

## Examples

Example of **incorrect** code:

```rust
fn my_func(count: u32) {
    if count == 0 {
        print!("Nothing to do");
        return;
    } else {
        print!("Moving on...");
    }
}
```

Example of **correct** code:

```rust
fn my_func(count: u32) {
    if count == 0 {
        print!("Nothing to do");
        return;
    }
    print!("Moving on...");
}
```

## Known problems

Some may prefer to keep the `else` block for clarity.

## Further Reading

* [Clippy - redundant_else](https://clippy.rust-lang.org/stable/index.html#redundant_else)
