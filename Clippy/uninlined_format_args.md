Pattern: Non-inlined format argument

Issue: -

## Description

Non-inlined code is slightly more difficult to read and understand,
as it requires arguments to be matched against the format string.
The inlined syntax, where allowed, is simpler.

## What it does

Detect when a variable is not inlined in a format string,
and suggests to inline it.

## Examples

```rust
format!("{}", var);
format!("{:?}", var);
format!("{v:?}", v = var);
format!("{0} {0}", var);
format!("{0:1$}", var, width);
format!("{:.*}", prec, var);
```
Use instead:
```rust
format!("{var}");
format!("{var:?}");
format!("{var:?}");
format!("{var} {var}");
format!("{var:width$}");
format!("{var:.prec$}");
```

If `allow-mixed-uninlined-format-args` is set to `false` in clippy.toml,
the following code will also trigger the lint:
```rust
format!("{} {}", var, 1+2);
```
Use instead:
```rust
format!("{var} {}", 1+2);
```

## Known Problems

If a format string contains a numbered argument that cannot be inlined
nothing will be suggested, e.g. `println!("{0}={1}", var, 1+2)`.

## Further Reading

* [Clippy - uninlined_format_args](https://clippy.rust-lang.org/stable/index.html#uninlined_format_args)
