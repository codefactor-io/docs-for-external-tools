Pattern: Use of `javascript:` URL scheme

Issue: -

## Description

Using URLs with the `javascript:` scheme creates security vulnerabilities through potential injection of unsanitized content. React 16.9+ warns about these URLs, and future versions will throw errors when encountering them.

## Examples

Example of **incorrect** code:
```jsx
<a href="javascript:void(0)">Test</a>
```

Example of **correct** code:
```jsx
<Foo test="javascript:void(0)" />
```