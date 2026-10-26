Pattern: Loop over single element

Issue: -

## Description

There is no reason to have a loop of a
single element.

## What it does

Checks whether a for loop has a single element.

## Examples

Example of **incorrect** code:

```rust
let item1 = 2;
for item in &[item1] {
    println!("{}", item);
}
```

Example of **correct** code:

```rust
let item1 = 2;
let item = &item1;
println!("{}", item);
```

## Further Reading

* [Clippy - single_element_loop](https://clippy.rust-lang.org/stable/index.html#single_element_loop)
