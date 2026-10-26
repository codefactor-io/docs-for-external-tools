Pattern: Use of `process::exit()` outside `main`

Issue: -

## Description

`exit()` immediately terminates the program with no information other than an exit code.
This provides no means to troubleshoot a problem, and may be an unexpected side effect.

Codebases may use this lint to require that all exits are performed either by panicking
(which produces a message, a code location, and optionally a backtrace)
or by calling `exit()` from `main()` (which is a single place to look).

## What it does

Detects calls to the `exit()` function that are not in the `main` function. Calls to `exit()`
immediately terminate the program.

## Examples

Example of **correct** code:

```rust
fn main() {
    std::process::exit(0);
}
```

Example of **incorrect** code:

```rust
fn main() {
    other_function();
}

fn other_function() {
    std::process::exit(0);
}
```

Use instead:

```rust
// To provide a stacktrace and additional information
panic!("message");

// or a main method with a return
fn main() -> Result<(), i32> {
    Ok(())
}
```

## Further Reading

* [Clippy - exit](https://clippy.rust-lang.org/stable/index.html#exit)
