Pattern: Use of `*_or` method with function call

Issue: -

## Description

The function will always be called. This is only bad if it allocates or
does some non-trivial amount of work.

## What it does

Checks for calls to `.or(foo(..))`, `.unwrap_or(foo(..))`,
`.or_insert(foo(..))` etc., and suggests to use `.or_else(|| foo(..))`,
`.unwrap_or_else(|| foo(..))`, `.unwrap_or_default()` or `.or_default()`
etc. instead.

## Examples

Example of **incorrect** code:

```rust
foo.unwrap_or(String::from("empty"));
```

Example of **correct** code:

```rust
foo.unwrap_or_else(|| String::from("empty"));
```

## Known problems

If the function has side-effects, not calling it will change the
semantic of the program, but you shouldn't rely on that.

The lint also cannot figure out whether the function you call is
actually expensive to call or not.

## Further Reading

* [Clippy - or_fun_call](https://clippy.rust-lang.org/stable/index.html#or_fun_call)
