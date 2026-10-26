Pattern: Side effect in zero-length repeat

Issue: -

## Description

Such an initialization, despite having a repeat length of 0, will still call the inner function.
This may not be obvious and as such there may be unintended side effects in code.

## What it does

Checks for array or vec initializations which contain an expression with side effects,
but which have a repeat count of zero.

## Examples

Example of **incorrect** code:

```rust
fn side_effect() -> i32 {
    println!("side effect");
    10
}
let a = [side_effect(); 0];
```

Example of **correct** code:

```rust
fn side_effect() -> i32 {
    println!("side effect");
    10
}
side_effect();
let a: [i32; 0] = [];
```

## Further Reading

* [Clippy - zero_repeat_side_effects](https://clippy.rust-lang.org/stable/index.html#zero_repeat_side_effects)
