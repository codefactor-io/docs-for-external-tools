Pattern: Missing scoping root for nesting selector

Issue: -

## Description

CSS nesting selectors (`&`) represent the parent selector in nested CSS. When used at the top level or within certain at-rules without a scoping root, they can cause unexpected behavior or indicate a mistake in the CSS structure.

## Examples

The following patterns are considered violations:

```css
@media all {
  & {}
}
```

The following patterns are *not* considered violations:

```css
a {
  @media all {
    & {}
  }
}
```

## Further Reading

* [stylelint - nesting-selector-no-missing-scoping-root](https://stylelint.io/user-guide/rules/nesting-selector-no-missing-scoping-root)