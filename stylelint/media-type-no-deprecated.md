Pattern: Deprecated media type

Issue: -

## Description

Several CSS media types defined in earlier specifications have been deprecated and should no longer be used. According to the CSS [media queries specification](https://drafts.csswg.org/mediaqueries-5/#media-types), the following media types are recognized as valid but match nothing:

- `aural`
- `braille`
- `embossed`
- `handheld`
- `projection`
- `speech`
- `tty`
- `tv`

Currently, the recommended media types are:

- `all`
- `screen`
- `print`

## Examples

The following patterns are considered violations:

```css
@media tty {}
```

The following patterns are *not* considered violations:

```css
@media screen {}
```

## Further Reading

* [stylelint - media-type-no-deprecated](https://stylelint.io/user-guide/rules/media-type-no-deprecated)