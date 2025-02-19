Pattern: Ambiguous link text

Issue: -

## Description

Link text should be descriptive and meaningful out of context. Words like "click here", "more", or "link" do not provide enough information for screen reader users to understand the link's purpose.

## Examples

Example of **incorrect** code:
```jsx
<a href="/article">click here</a>
<a href="/docs">read more</a>
<a href="/page">link</a>
```

Example of **correct** code:
```jsx
<a href="/article">read full article about accessibility</a>
<a href="/docs">view documentation</a>
<a href="/page" aria-label="Download user guide">download</a>
```