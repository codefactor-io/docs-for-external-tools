Pattern: Component created during render

Issue: -

## Description

A component created during render gets a new identity on every render,
so React unmounts and remounts it each time — resetting all of its
state and re-rendering its entire subtree.

## Examples

Example of **incorrect** code:
```jsx
function Example(props) {
  const Component = createComponent();
  return <Component />;
}
```

Example of **correct** code:
```jsx
function Inner(props) {
  return <div>{props.text}</div>;
}
function Outer() {
  return <Inner text="hello" />;
}
```
