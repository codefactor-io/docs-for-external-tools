Pattern: Invalid prelude for at-rule

Issue: -

## Description

Disallow invalid preludes for at-rules.

This rule considers preludes for at-rules defined within the CSS specifications, up to and including Editor's Drafts, to be valid.

## Examples

The following patterns are considered violations:

```css
@property foo {}
```

```css
@font-palette-values foo {}
```

The following patterns are *not* considered violations:

```css
@property --foo {}
```

```css
@font-palette-values --foo {}
```

## Further Reading

* [stylelint - at-rule-prelude-no-invalid](https://stylelint.io/user-guide/rules/at-rule-prelude-no-invalid)