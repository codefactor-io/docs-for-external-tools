Pattern: Invalid DOM property name

Issue: -

## Description

React uses camelCase property names and specific DOM attributes. Using unknown property names or incorrect attribute syntax (like HTML's `class` instead of `className`) will have no effect and may indicate errors.

## Examples

Example of **incorrect** code:
```jsx
const Hello = <div class="hello">Hello World</div>;
const Alphabet = <div abc="something">Alphabet</div>;
const IconButton = <div aria-foo="bar" />;
```

Example of **correct** code:
```jsx
const Hello = <div className="hello">Hello World</div>;
const IconButton = <div aria-label="bar" />;
```