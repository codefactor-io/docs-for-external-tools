Pattern: Missing type annotations on `transmute()`

Issue: -

## Description

If not, one or more unexpected types could be used during `transmute()`, potentially leading
to Undefined Behavior or other problems.

This is particularly dangerous in case a seemingly innocent/unrelated change causes type
inference to result in a different type. For example, if `transmute()` is the tail
expression of an `if`-branch, and the `else`-branch type changes, the compiler may silently
infer a different type to be returned by `transmute()`. That is because the compiler is
free to change the inference of a type as long as that inference is technically correct,
regardless of the programmer's unknown expectation.

Both type-parameters, the input- and the output-type, to any `transmute()` should
be given explicitly: Setting the input-type explicitly avoids confusion about what the
argument's type actually is. Setting the output-type explicitly avoids type-inference
to infer a technically correct yet unexpected type.

## What it does

Checks if transmute calls have all generics specified.

## Examples

Example of **incorrect** code:

```rust
let mut x: i32 = 0;
// Avoid "naked" calls to `transmute()`!
x = std::mem::transmute([1u16, 2u16]);

// `first_answers` is intended to transmute a slice of bool to a slice of u8.
// But the programmer forgot to index the first element of the outer slice,
// so we are actually transmuting from "pointers to slices" instead of
// transmuting from "a slice of bool", causing a nonsensical result.
let the_answers: &[&[bool]] = &[&[true, false, true]];
let first_answers: &[u8] = std::mem::transmute(the_answers);
```

Example of **correct** code:

```rust
let x = std::mem::transmute::<[u16; 2], i32>([1u16, 2u16]);

// The explicit type parameters on `transmute()` makes the intention clear,
// and cause a type-error if the actual types don't match our expectation.
let the_answers: &[&[bool]] = &[&[true, false, true]];
let first_answers: &[u8] = std::mem::transmute::<&[bool], &[u8]>(the_answers[0]);
```

## Further Reading

* [Clippy - missing_transmute_annotations](https://clippy.rust-lang.org/stable/index.html#missing_transmute_annotations)
