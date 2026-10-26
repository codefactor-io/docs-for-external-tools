Pattern: `Result::map()` with unit function

Issue: -

## Description

Readability, this can be written more clearly with
an if let statement

## What it does

Checks for usage of `result.map(f)` where f is a function
or closure that returns the unit type `()`.

## Examples

Example of **incorrect** code:

```rust
let x: Result<String, String> = do_stuff();
x.map(log_err_msg);
x.map(|msg| log_err_msg(format_msg(msg)));
```

Example of **correct** code:

```rust
let x: Result<String, String> = do_stuff();
if let Ok(msg) = x {
    log_err_msg(msg);
};
if let Ok(msg) = x {
    log_err_msg(format_msg(msg));
};
```

## Further Reading

* [Clippy - result_map_unit_fn](https://clippy.rust-lang.org/stable/index.html#result_map_unit_fn)
