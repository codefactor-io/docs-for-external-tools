Pattern: Use of `write!` instead of `print!`

Issue: -

## Description

Using `(e)println!` is clearer and more concise

## What it does

Checks for usage of `write!()` / `writeln()!` which can be
replaced with `(e)print!()` / `(e)println!()`

## Examples

Example of **incorrect** code:

```rust
writeln!(&mut std::io::stderr(), "foo: {:?}", bar).unwrap();
writeln!(&mut std::io::stdout(), "foo: {:?}", bar).unwrap();
```

Example of **correct** code:

```rust
eprintln!("foo: {:?}", bar);
println!("foo: {:?}", bar);
```

## Further Reading

* [Clippy - explicit_write](https://clippy.rust-lang.org/stable/index.html#explicit_write)
