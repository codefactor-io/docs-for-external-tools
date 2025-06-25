Pattern: Unknown value for media feature

Issue: -

## Description

Disallow unknown values for media features.

```css
@media (color: red) {}
/**     ↑      ↑
 * feature and value pairs like these */
```

This rule considers values for media features defined within the CSS specifications to be known.

## Examples

The following pattern are considered violations:

```css
@media (color: red) { top: 1px; }
```

```css
@media (width: 10) { top: 1px; }
```

```css
@media (width: auto) { top: 1px; }
```

The following patterns are *not* considered violations:

```css
@media (color: 8) { top: 1px; }
```

```css
@media (width: 10px) { top: 1px; }
```

## Further Reading

* [stylelint - media-feature-name-value-no-unknown](https://stylelint.io/user-guide/rules/media-feature-name-value-no-unknown/)