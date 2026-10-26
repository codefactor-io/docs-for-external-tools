Pattern: Unicode literal not in NFC form

Issue: -

## Description

If such a string is compared to another, the results
may be surprising.

## What it does

Checks for string literals that contain Unicode in a form
that is not equal to its
[NFC-recomposition](http://www.unicode.org/reports/tr15/#Norm_Forms).

## Examples

You may not see it, but "à"" and "à"" aren't the same string. The
former when escaped is actually `"a\u{300}"` while the latter is `"\u{e0}"`.

## Further Reading

* [Clippy - unicode_not_nfc](https://clippy.rust-lang.org/stable/index.html#unicode_not_nfc)
