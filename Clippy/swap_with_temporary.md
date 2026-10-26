Pattern: `mem::swap()` with temporary value

Issue: -

## Description

Storing a new value in place of a temporary value which will
be dropped right after the `swap` is an inefficient way of performing
an assignment. The same result can be achieved by using a regular
assignment.

## What it does

Checks for usage of `std::mem::swap` with temporary values.

## Examples

```rust
fn replace_string(s: &mut String) {
    std::mem::swap(s, &mut String::from("replaced"));
}
```
Use instead:
```rust
fn replace_string(s: &mut String) {
    *s = String::from("replaced");
}
```

Also, swapping two temporary values has no effect, as they will
both be dropped right after swapping them. This is likely an indication
of a bug. For example, the following code swaps the references to
the last element of the vectors, instead of swapping the elements
themselves:

```rust
fn bug(v1: &mut [i32], v2: &mut [i32]) {
    // Incorrect: swapping temporary references (`&mut &mut` passed to swap)
    std::mem::swap(&mut v1.last_mut().unwrap(), &mut v2.last_mut().unwrap());
}
```
Use instead:
```rust
fn correct(v1: &mut [i32], v2: &mut [i32]) {
    std::mem::swap(v1.last_mut().unwrap(), v2.last_mut().unwrap());
}
```

## Further Reading

* [Clippy - swap_with_temporary](https://clippy.rust-lang.org/stable/index.html#swap_with_temporary)
