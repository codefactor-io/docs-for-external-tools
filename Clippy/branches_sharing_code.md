Pattern: Code duplicated in all branches

Issue: -

## Description

Duplicate code is less maintainable.

## What it does

Checks if the blocks of an `if`/`else`, or the arms of a `match`, contain shared code that
can be moved out of the branches.

## Examples

```rust
let foo = if … {
    println!("Hello World");
    13
} else {
    println!("Hello World");
    42
};
```

Use instead:
```rust
println!("Hello World");
let foo = if … {
    13
} else {
    42
};
```

For a `match`, when every arm ends with the same expression it can be moved after the
`match`:
```rust
match mode {
    Mode::A => { a(); Ok(()) }
    Mode::B => { b(); Ok(()) }
}
```

Use instead:
```rust
match mode {
    Mode::A => { a(); }
    Mode::B => { b(); }
}
Ok(())
```

## Further Reading

* [Clippy - branches_sharing_code](https://clippy.rust-lang.org/stable/index.html#branches_sharing_code)
