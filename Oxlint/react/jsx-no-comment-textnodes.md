Pattern: Comment string in JSX text node

Issue: -

## Description

JSX treats any text within elements as literal content to be rendered. This can cause comments (starting with `//` or `/*`) to appear as unwanted text in the output instead of being treated as comments when not properly wrapped in curly braces.

## Examples

Example of **incorrect** code:
```jsx
const Hello = () => {
  return <div>// empty div</div>;
};

const Hello = () => {
  return <div>/* empty div */</div>;
};
```

Example of **correct** code:
```jsx
const Hello = () => {
  return <div>{/* empty div */}</div>;
};
```