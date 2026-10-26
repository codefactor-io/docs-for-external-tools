Pattern: Too many `bool` function parameters

Issue: -

## Description

Boolean parameters obscure meaning at the call site. The reader has to
remember what each `true` or `false` means and which position each flag
belongs in, with no help from the type system.

The best replacement depends on what role the bool plays:

- Use a two-variant enum when one parameter selects a mode.
- Split one function into two named operations when the choices are
  distinct actions.
- Group multiple related flags into a struct or options type when they
  travel together.
- Move the setting onto `self` or an existing config/context parameter
  when it is really part of the surrounding state.

This optimizes for readability of the calling code, which future readers
encounter more often than the function declaration.

The `max-fn-params-bools` configuration accepts `0`, which lints on any
function with a bool parameter.

## What it does

Checks for excessive use of bools in function declarations.

## Examples

Example of **incorrect** code:

```rust
fn render_document(show_hidden: bool, is_draft: bool) { ... }
```

Example of **correct** code:

```rust
enum Visibility {
    ShowHidden,
    HideHidden,
}

enum DocumentKind {
    Draft,
    Final,
}

fn render_document(visibility: Visibility, kind: DocumentKind) { ... }

// or split the operation when the choices are distinct
fn render_draft() { ... }
fn render_final() { ... }
```

## Further Reading

* [Clippy - fn_params_excessive_bools](https://clippy.rust-lang.org/stable/index.html#fn_params_excessive_bools)
