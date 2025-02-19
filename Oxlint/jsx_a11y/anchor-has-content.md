Pattern: Empty anchor

Issue: -

## Description

Anchor elements must have content that is accessible to screen readers. This can be text content, elements with valid aria labels, or elements that are not hidden from screen readers.

## Examples

Example of **incorrect** code:
```jsx
<a href="/page"></a>
<a href="/home"><span aria-hidden="true">Home</span></a>
<a href="/profile" />
```

Example of **correct** code:
```jsx
<a href="/page">Visit Page</a>
<a href="/home" aria-label="Return to home page">
  <IconHome aria-hidden="true" />
</a>
<a href="/profile" title="View profile">
  <img src="avatar.png" alt="Profile" />
</a>
```