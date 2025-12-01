Pattern: Malformed dependencies for `useEffect`

Issue: -

## Description

React Hooks like `useEffect` and similar require a list of dependencies to be passed as an argument. This list is used to determine when the effect should be re-run. If the list is missing or incomplete, the effect may run more often than necessary, or not at all.

## Examples

Example of **incorrect** code:

```jsx
function MyComponent(props) {
  useEffect(() => {
    console.log(props.foo);
  }, []);
  // `props` is missing from the dependencies array
  return <div />;
}
```

Example of **correct** code:

```jsx
function MyComponent(props) {
  useEffect(() => {
    console.log(props.foo);
  }, [props]);
  return <div />;
}
```