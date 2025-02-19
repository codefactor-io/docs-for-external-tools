Pattern: Missing dependency in Hook dependency array

Issue: -

## Description

React Hooks like `useEffect` require a complete list of dependencies to function correctly. Missing dependencies can cause stale closures, leading to bugs where effects don't run when they should or run with outdated values.

## Examples

Example of **incorrect** code:
```javascript
function MyComponent(props) {
  useEffect(() => {
    console.log(props.foo);
  }, []); // `props` is missing from deps array
  return <div />;
}
```

Example of **correct** code:
```javascript
function MyComponent(props) {
  useEffect(() => {
    console.log(props.foo);
  }, [props]);
  return <div />;
}
```