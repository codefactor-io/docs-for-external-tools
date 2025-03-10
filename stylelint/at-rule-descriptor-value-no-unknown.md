Pattern: Unknown value for descriptor within at-rule

Issue: -

## Description

Disallow unknown values for descriptors within at-rules.

This rule considers descriptors and values defined in the CSS Specifications, up to and including Editor's Drafts, to be known.

## Examples

The following patterns are considered violations:

```css
@counter-style foo {
  system: unknown;
}
```

The following patterns are *not* considered violations:

```css
@counter-style foo {
  system: numeric;
}
```

## Further Reading

* [stylelint - at-rule-descriptor-value-no-unknown](https://stylelint.io/user-guide/rules/at-rule-descriptor-value-no-unknown)