Pattern: Missing use of `pop_if()`

Issue: -

## Description

Using `pop_if` is more concise and idiomatic.

## What it does

Checks for code to be replaced by `pop_if` methods.

## Examples

Example of **incorrect** code:

```rust
if vec.last().is_some_and(|x| *x > 5) {
    vec.pop().unwrap();
}
if deque.back().is_some_and(|x| *x > 5) {
    deque.pop_back().unwrap();
}
if deque.front().is_some_and(|x| *x > 5) {
    deque.pop_front().unwrap();
}
```

Example of **correct** code:

```rust
vec.pop_if(|x| *x > 5);
deque.pop_back_if(|x| *x > 5);
deque.pop_front_if(|x| *x > 5);
```

## Known issues

When the popped value is assigned or used in an expression,
or when the `if` condition is part of an `else if` branch, the
lint will trigger but will not provide an automatic suggestion.

## Further Reading

* [Clippy - manual_pop_if](https://clippy.rust-lang.org/stable/index.html#manual_pop_if)
