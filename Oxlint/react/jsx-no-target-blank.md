Pattern: Unsafe `target="_blank"` usage

Issue: -

## Description

Using `target="_blank"` without `rel="noreferrer"` creates a security vulnerability. The opened link can access the original window's `window.opener` property and potentially redirect to malicious sites. Adding `rel="noreferrer"` prevents this security issue.

## Examples

Example of **incorrect** code:
```jsx
<a target="_blank" href="https://example.com/"></a>
<a target="_blank" href={dynamicLink}></a>
```

Example of **correct** code:
```jsx
<a target="_blank" rel="noreferrer" href="https://example.com"></a>
<a target="_blank" rel="noopener noreferrer" href="https://example.com"></a>
<a target="_blank" href="/absolute/path/in/the/host"></a>
```