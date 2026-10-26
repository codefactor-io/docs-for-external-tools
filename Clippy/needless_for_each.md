Pattern: Use of `for_each()` instead of `for` loop

Issue: -

## Description

`for_each` may be used after applying iterator transformers like
`filter` for better readability and performance. It may also be used to fit a simple
operation on one line.
But when none of these apply, a simple `for` loop is more idiomatic.

## What it does

Checks for usage of `for_each` that would be more simply written as a
`for` loop.

## Examples

Example of **incorrect** code:

```rust
let v = vec![0, 1, 2];
v.iter().for_each(|elem| {
    println!("{elem}");
})
```

Example of **correct** code:

```rust
let v = vec![0, 1, 2];
for elem in &v {
    println!("{elem}");
}
```

## Known Problems

When doing things such as:
```rust
let v = vec![0, 1, 2];
v.iter().for_each(|elem| unsafe {
    libc::printf(c"%d\n".as_ptr(), elem);
});
```
This lint will not trigger.

## Further Reading

* [Clippy - needless_for_each](https://clippy.rust-lang.org/stable/index.html#needless_for_each)
