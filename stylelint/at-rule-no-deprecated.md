Pattern: Deprecated at-rule

Issue: -

## Description

This rule flags at-rules that were removed or deprecated after being in the CSS specifications, including editor drafts, and were subsequently either:

    shipped in a stable version of a browser
    shipped by a developer channel/edition browser
    shipped but behind experimental flags
    polyfilled with some adoption before any browser actually shipped
    had an MDN page at one point in time


## Examples

The following patterns are considered violations:

```css
@viewport {}
```

```css
a { @apply foo; }
```

The following patterns are *not* considered violations:

```css
@starting-style {}
```

```css
a { @layer {} }
```
