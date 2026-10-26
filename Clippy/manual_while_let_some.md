Pattern: Missing use of `while let` with `pop()`

Issue: -

## Description

Such loops can be written in a more idiomatic way by using a while-let loop and directly
pattern matching on the return value of `Vec::pop()`.

## What it does

Looks for loops that check for emptiness of a `Vec` in the condition and pop an element
in the body as a separate operation.

## Examples

Example of **incorrect** code:

```rust
let mut numbers = vec![1, 2, 3, 4, 5];
while !numbers.is_empty() {
    let number = numbers.pop().unwrap();
    // use `number`
}
```

Example of **correct** code:

```rust
let mut numbers = vec![1, 2, 3, 4, 5];
while let Some(number) = numbers.pop() {
    // use `number`
}
```

## Further Reading

* [Clippy - manual_while_let_some](https://clippy.rust-lang.org/stable/index.html#manual_while_let_some)
