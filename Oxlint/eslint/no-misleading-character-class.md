Pattern: Misleading character class

Issue: -

## Description

Unicode includes characters which are made by multiple code points.
RegExp character class syntax (`/[abc]/`) cannot handle characters
which are made by multiple code points as a character;
those characters will be dissolved to each code point.
For example, `❇️` is made by `❇` (`U+2747`) and VARIATION SELECTOR-16 (`U+FE0F`).
If this character is in a RegExp character class,
it will match either `❇` (`U+2747`) or VARIATION SELECTOR-16 (`U+FE0F`) rather than `❇️`.

This can lead to regular expressions that do not match what the author intended,
especially for emoji, regional indicators, and characters with combining marks.

## Examples

Example of **incorrect** code:

```javascript
/^[Á]$/u;
/^[❇️]$/u;
/^[👶🏻]$/u;
/^[🇯🇵]$/u;
/^[👨‍👩‍👦]$/u;
/^[👍]$/;
new RegExp("[🎵]");
```

Example of **correct** code:

```javascript
/^[abc]$/;
/^[👍]$/u;
/[\u00B7\u0300-\u036F]/u;
new RegExp("^[\u{1F1EF}\u{1F1F5}]", "u");
```