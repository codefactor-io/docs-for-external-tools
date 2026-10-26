Pattern: Use of `expect()` with function call

Issue: -

## Description

The function will always be called.

## What it does

Checks for calls to `.expect(&format!(...))`, `.expect(foo(..))`,
etc., and suggests to use `unwrap_or_else` instead

## Examples

Example of **incorrect** code:

```rust
foo.expect(&format!("Err {}: {}", err_code, err_msg));

// or

foo.expect(format!("Err {}: {}", err_code, err_msg).as_str());
```

Example of **correct** code:

```rust
foo.unwrap_or_else(|| panic!("Err {}: {}", err_code, err_msg));
```

## Known problems

If the function has side-effects, not calling it will
change the semantics of the program, but you shouldn't rely on that anyway.

## Further Reading

* [Clippy - expect_fun_call](https://clippy.rust-lang.org/stable/index.html#expect_fun_call)
