Pattern: Role attribute instead of semantic tag

Issue: -

## Description

Use semantic HTML elements instead of ARIA roles on generic elements. Semantic elements provide better accessibility and are more maintainable than ARIA roles on generic elements.

## Examples

Example of **incorrect** code:
```jsx
<div role="button" />
<span role="heading" />
<div role="article" />
```

Example of **correct** code:
```jsx
<button />
<h1 />
<article />
```