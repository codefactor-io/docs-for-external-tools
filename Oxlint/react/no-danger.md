Pattern: Use of `dangerouslySetInnerHTML`

Issue: -

## Description

The `dangerouslySetInnerHTML` prop allows injection of raw HTML into React components, creating potential XSS vulnerabilities. Use React's built-in escaping mechanisms and component composition instead.

## Examples

Example of **incorrect** code:
```jsx
const Hello = <div dangerouslySetInnerHTML={{ __html: "Hello World" }}></div>;
```

Example of **correct** code:
```jsx
const Hello = <div>Hello World</div>;
```