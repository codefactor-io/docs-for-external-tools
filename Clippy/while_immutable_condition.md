Pattern: Immutable `while` loop condition

Issue: -

## Description

If the condition is unchanged, entering the body of the loop
will lead to an infinite loop.

## What it does

Checks whether variables used within while loop condition
can be (and are) mutated in the body.

## Examples

Example of **incorrect** code:

```rust
let i = 0;
while i > 10 {
    println!("let me loop forever!");
}
```

## Known problems

If the `while`-loop is in a closure, the check for mutation of the
condition variables in the body can cause false negatives. For example when only `Upvar` `a` is
in the condition and only `Upvar` `b` gets mutated in the body, the lint will not trigger.

## Further Reading

* [Clippy - while_immutable_condition](https://clippy.rust-lang.org/stable/index.html#while_immutable_condition)
