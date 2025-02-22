Pattern: Missing newline after declaration colon

Issue: -

## Description

Require a newline or disallow whitespace after the colon of declarations.

```css
a {
  box-shadow:
    0 0 0 1px #5b9dd9,
    0 0 2px 1px rgba(30, 140, 190, 0.8);
}        /* ↑ */
/**         ↑
 * The newline after this colon */
```

## Examples

`string`: `"always"|"always-multi-line"`

### `"always"`

There _must always_ be a newline after the colon.

The following patterns are considered problems:

```css
a { color:pink; }
```

```css
a { color: pink; }
```

The following patterns are _not_ considered problems:

```css
a {
  color:
    pink;
}
```

### `"always-multi-line"`

There _must always_ be a newline after the colon _if the declaration's value is multi-line_.

The following patterns are considered problems:

```css
a {
  box-shadow: 0 0 0 1px #5b9dd9,
    0 0 2px 1px rgba(30, 140, 190, 0.8);
}
```

The following patterns are _not_ considered problems:

```css
a {
  box-shadow:
    0 0 0 1px #5b9dd9,
    0 0 2px 1px rgba(30, 140, 190, 0.8);
}
```

```css
a {
  color: pink;
}
```

## Further Reading

* [stylelint - declaration-colon-newline-after](https://stylelint.io/user-guide/rules/declaration-colon-newline-after)