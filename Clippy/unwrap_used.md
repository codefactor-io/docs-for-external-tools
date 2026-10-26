Pattern: Use of `unwrap()`

Issue: -

## Description

It is better to handle the `None` or `Err` case,
or at least call `.expect(_)` with a more helpful message. Still, for a lot of
quick-and-dirty code, `unwrap` is a good choice, which is why this lint is
`Allow` by default.

`result.unwrap()` will let the thread panic on `Err` values.
Normally, you want to implement more sophisticated error handling,
and propagate errors upwards with `?` operator.

Even if you want to panic on errors, not all `Error`s implement good
messages on display. Therefore, it may be beneficial to look at the places
where they may get displayed. Activate this lint to do just that.

## What it does

Checks for `.unwrap()` or `.unwrap_err()` calls on `Result`s and `.unwrap()` call on `Option`s.

## Examples

```rust
option.unwrap();
result.unwrap();
```

Use instead:
```rust
option.expect("more helpful message");
result.expect("more helpful message");
```

If [expect_used](#expect_used) is enabled, instead:
```rust
option?;

// or

result?;
```

## Further Reading

* [Clippy - unwrap_used](https://clippy.rust-lang.org/stable/index.html#unwrap_used)
