Pattern: Single-arm `match` used for destructuring

Issue: -

## Description

Just readability – `let` doesn't nest, whereas a `match` does.

## What it does

Checks for matches being used to destructure a single-variant enum
or tuple struct where a `let` will suffice.

## Examples

Example of **incorrect** code:

```rust
enum Wrapper {
    Data(i32),
}

let wrapper = Wrapper::Data(42);

let data = match wrapper {
    Wrapper::Data(i) => i,
};
```

Example of **correct** code:

```rust
enum Wrapper {
    Data(i32),
}

let wrapper = Wrapper::Data(42);
let Wrapper::Data(data) = wrapper;
```

## Further Reading

* [Clippy - infallible_destructuring_match](https://clippy.rust-lang.org/stable/index.html#infallible_destructuring_match)
