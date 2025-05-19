Pattern: Inconsistent lightness notation

Issue: -

## Description

Specify number or percentage notation for lightness.

```css
    a { color: oklch(85% 0.17 88) }
/**                  ↑
 *                   This notation */
```

This rule supports `oklch`, `oklab`, `lch` and `lab` functions.

## Examples

### `"percentage"`

Lightness _must always_ use the percentage notation.

```json
{
  "lightness-notation": "percentage"
}
```

The following patterns are considered problems:

<!-- prettier-ignore -->
```css
a { color: oklch(0.85 0.17 88) }
```

<!-- prettier-ignore -->
```css
a { color: oklab(0.86 0.2 154) }
```

<!-- prettier-ignore -->
```css
a { color: lch(85 0.17 88) }
```

<!-- prettier-ignore -->
```css
a { color: lab(86 0.2 154) }
```

The following patterns are _not_ considered problems:

<!-- prettier-ignore -->
```css
a { color: oklch(85% 0.17 88) }
```

<!-- prettier-ignore -->
```css
a { color: oklab(86% 0.2 154) }
```

<!-- prettier-ignore -->
```css
a { color: lch(85% 0.17 88) }
```

<!-- prettier-ignore -->
```css
a { color: lab(86% 0.2 154) }
```

### `"number"`

Lightness _must always_ use the number notation.

```json
{
  "lightness-notation": "number"
}
```

The following patterns are considered problems:

<!-- prettier-ignore -->
```css
a { color: oklch(85% 0.17 88) }
```

<!-- prettier-ignore -->
```css
a { color: oklab(86% 0.2 154) }
```

<!-- prettier-ignore -->
```css
a { color: lch(85% 0.17 88) }
```

<!-- prettier-ignore -->
```css
a { color: lab(86% 0.2 154) }
```

The following patterns are _not_ considered problems:

<!-- prettier-ignore -->
```css
a { color: oklch(0.85 0.17 88) }
```

<!-- prettier-ignore -->
```css
a { color: oklab(0.86 0.2 154) }
```

<!-- prettier-ignore -->
```css
a { color: lch(85 0.17 88) }
```

<!-- prettier-ignore -->
```css
a { color: lab(86 0.2 154) }
```

## Further Reading

* [stylelint - lightness-notation](https://stylelint.io/user-guide/rules/lightness-notation)