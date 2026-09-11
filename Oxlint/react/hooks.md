Pattern: Invalid Hook call

Issue: -

## Description

React tracks hook state by call order. A hook that is called
conditionally or in a different order between renders breaks the
association between each hook call and its state, corrupting
component state.

## Examples

Example of **incorrect** code:
```jsx
function Component(props) {
  if (props.cond) {
    useState(0); // hooks may not be called conditionally
  }
  return <div>{props.text}</div>;
}
```

Example of **correct** code:
```jsx
function Component(props) {
  const [state, setState] = useState(0);
  return <div onClick={() => setState(state + 1)}>{props.text}</div>;
}
```
