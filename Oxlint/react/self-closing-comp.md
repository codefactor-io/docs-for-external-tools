Pattern: Unnecessary closing tag on empty component

Issue: -

## Description

Components without children should use self-closing tags to improve readability and reduce unnecessary markup. A closing tag is only needed when the component contains content or whitespace with newlines.

## Examples

Example of **incorrect** code:
```jsx
const elem = <Component linter="oxlint"></Component>;
const dom_elem = <div id="oxlint"></div>;
const welem = <div id="oxlint"></div>;
```

Example of **correct** code:
```jsx
const elem = <Component linter="oxlint" />;
const welem = <Component linter="oxlint"> </Component>;
const dom_elem = <div id="oxlint" />;
```