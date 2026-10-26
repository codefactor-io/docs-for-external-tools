Pattern: `Option::map()` with unit-returning function

Issue: -

## Description

Readability, this can be written more clearly with
an if let statement

## What it does

Checks for usage of `option.map(f)` where f is a function
or closure that returns the unit type `()`.

## Examples

Example of **incorrect** code:

```rust
let x: Option<String> = do_stuff();
x.map(log_err_msg);
x.map(|msg| log_err_msg(format_msg(msg)));
```

Example of **correct** code:

```rust
let x: Option<String> = do_stuff();
if let Some(msg) = x {
    log_err_msg(msg);
}

if let Some(msg) = x {
    log_err_msg(format_msg(msg));
}
```

## Further Reading

* [Clippy - option_map_unit_fn](https://clippy.rust-lang.org/stable/index.html#option_map_unit_fn)
