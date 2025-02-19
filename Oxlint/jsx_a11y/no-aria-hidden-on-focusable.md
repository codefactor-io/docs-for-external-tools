Pattern: Hidden focusable element

Issue: -

## Description

Setting aria-hidden="true" on focusable elements creates a confusing experience for screen reader users since the element can still receive focus but is hidden from the accessibility tree.

## Examples

Example of **incorrect** code:
```jsx
<button aria-hidden="true">Click me</button>
<div aria-hidden="true" tabIndex="0">Focusable</div>
<a href="/page" aria-hidden="true">Link</a>
```

Example of **correct** code:
```jsx
<button>Click me</button>
<div aria-hidden="true">Not focusable</div>
<a href="/page">Link</a>
```