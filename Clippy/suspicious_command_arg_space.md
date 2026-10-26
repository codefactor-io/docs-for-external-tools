Pattern: `Command::arg()` with space-separated arguments

Issue: -

## Description

`Command::arg()` does not split arguments by space. An argument like `arg("-t ext2")`
will be passed as a single argument to the command,
which is likely not what was intended.

## What it does

Checks for `Command::arg()` invocations that look like they
should be multiple arguments instead, such as `arg("-t ext2")`.

## Examples

Example of **incorrect** code:

```rust
std::process::Command::new("echo").arg("-n hello").spawn().unwrap();
```

Example of **correct** code:

```rust
std::process::Command::new("echo").args(["-n", "hello"]).spawn().unwrap();
```

## Further Reading

* [Clippy - suspicious_command_arg_space](https://clippy.rust-lang.org/stable/index.html#suspicious_command_arg_space)
