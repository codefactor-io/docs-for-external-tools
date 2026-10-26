Pattern: Use of `expect()` on `Result` or `Option`

Issue: -

## Description

Usually it is better to handle the `None` or `Err` case.
Still, for a lot of quick-and-dirty code, `expect` is a good choice, which is why
this lint is `Allow` by default.

`result.expect()` will let the thread panic on `Err`
values. Normally, you want to implement more sophisticated error handling,
and propagate errors upwards with `?` operator.

## What it does

Checks for `.expect()` or `.expect_err()` calls on `Result`s and `.expect()` call on `Option`s.

## Examples

Example of **incorrect** code:

```rust
option.expect("one");
result.expect("one");
```

Example of **correct** code:

```rust
option?;

// or

result?;
```

## Further Reading

* [Clippy - expect_used](https://clippy.rust-lang.org/stable/index.html#expect_used)
