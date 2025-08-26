Pattern: Redundant nested style rule within block

Issue: -

## Description

```css
a { & { color: red; } }
/** ↑
 * This nested style rule */
```

## Examples

The following patterns are considered violations:

<!-- prettier-ignore -->
```css
a { & { color: red; } }
```

<!-- prettier-ignore -->
```css
a { @media all { & { color: red; } } }
```

The following patterns are *not* considered violations:

<!-- prettier-ignore -->
```css
a { color: red; }
```

<!-- prettier-ignore -->
```css
a { @media all { color: red; } }
```

<!-- prettier-ignore -->
```css
a { &.foo { color: red; } }
```

## Further Reading

* [stylelint - block-no-redundant-nested-style-rules](https://stylelint.io/user-guide/rules/block-no-redundant-nested-style-rules)