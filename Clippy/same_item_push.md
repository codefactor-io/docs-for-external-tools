Pattern: Same item pushed in loop

Issue: -

## Description

This kind of operation can be expressed more succinctly with
`vec![item; SIZE]` or `vec.resize(NEW_SIZE, item)` and using these alternatives may also
have better performance.

## What it does

Checks whether a for loop is being used to push a constant
value into a Vec.

## Examples

Example of **incorrect** code:

```rust
let item1 = 2;
let item2 = 3;
let mut vec: Vec<u8> = Vec::new();
for _ in 0..20 {
    vec.push(item1);
}
for _ in 0..30 {
    vec.push(item2);
}
```

Example of **correct** code:

```rust
let item1 = 2;
let item2 = 3;
let mut vec: Vec<u8> = vec![item1; 20];
vec.resize(20 + 30, item2);
```

## Further Reading

* [Clippy - same_item_push](https://clippy.rust-lang.org/stable/index.html#same_item_push)
