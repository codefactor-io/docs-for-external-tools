Pattern: Unnecessary `?` in `Ok(x?)` or `Some(x?)`

Issue: -

## Description

There's no reason to use `?` to short-circuit when execution of the body will end there anyway.

## What it does

Suggests replacing `Ok(x?)` or `Some(x?)` with `x` in return positions where the `?` operator
is not needed to convert the type of `x`.

## Examples

Example of **incorrect** code:

```rust
fn f(s: &str) -> Option<usize> {
    Some(s.find('x')?)
}

fn g(s: &str) -> Result<usize, ParseIntError> {
    Ok(s.parse()?)
}
```

Example of **correct** code:

```rust
fn f(s: &str) -> Option<usize> {
    s.find('x')
}

fn g(s: &str) -> Result<usize, ParseIntError> {
    s.parse()
}
```

## Further Reading

* [Clippy - needless_question_mark](https://clippy.rust-lang.org/stable/index.html#needless_question_mark)
