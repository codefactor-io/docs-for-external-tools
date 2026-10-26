Pattern: Collapsible nested `match` or `if let`

Issue: -

## Description

It is unnecessarily verbose and complex.

## What it does

Finds nested `match` or `if let` expressions where the patterns may be "collapsed" together
without adding any branches.

Note that this lint is not intended to find _all_ cases where nested match patterns can be merged, but only
cases where merging would most likely make the code more readable.

## Examples

Example of **incorrect** code:

```rust
fn func(opt: Option<Result<u64, String>>) {
    let n = match opt {
        Some(n) => match n {
            Ok(n) => n,
            _ => return,
        }
        None => return,
    };
}
```

Example of **correct** code:

```rust
fn func(opt: Option<Result<u64, String>>) {
    let n = match opt {
        Some(Ok(n)) => n,
        _ => return,
    };
}
```

## Further Reading

* [Clippy - collapsible_match](https://clippy.rust-lang.org/stable/index.html#collapsible_match)
