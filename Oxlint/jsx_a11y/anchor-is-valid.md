Pattern: Invalid anchor usage

Issue: -

## Description

Anchor (<a>) elements should only be used for navigation with valid href attributes. For click handlers and other interactions, use button elements instead. Invalid href values or anchors with click handlers can break keyboard navigation and hurt SEO.

## Examples

Example of **incorrect** code:
```jsx
<a onClick={handleClick}>
  Click me
</a>

<a href="#">
  Trigger action
</a>

<a href="javascript:void(0)">
  Do something
</a>
```

Example of **correct** code:
```jsx
<a href="/page">
  Go to page
</a>

<button onClick={handleClick}>
  Trigger action
</button>

<a href="https://example.com">
  Visit site
</a>
```