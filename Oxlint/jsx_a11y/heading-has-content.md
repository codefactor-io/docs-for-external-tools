Pattern: Empty heading

Issue: -

## Description

Heading elements must have content that is accessible to screen readers. Empty headings or headings with content hidden from screen readers create confusion about the page structure.

## Examples

Example of **incorrect** code:
```jsx
<h1></h1>
<h2 />
<h3><span aria-hidden="true">Hidden</span></h3>
```

Example of **correct** code:
```jsx
<h1>Main Title</h1>
<h2>Section Title</h2>
<h3>
  <Icon aria-hidden="true" />
  Subsection Title
</h3>
```