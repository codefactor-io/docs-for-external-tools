Pattern: Use of `ReactDOM.render()` return value

Issue: -

## Description

Using the return value from `ReactDOM.render()` is a legacy feature that should be avoided. Modern React applications should use refs or other methods to access component instances.

## Examples

Example of **incorrect** code:
```jsx
var inst = ReactDOM.render(<App />, document.body);
function render() {
  return ReactDOM.render(<App />, document.body);
}
```

Example of **correct** code:
```jsx
ReactDOM.render(<App />, document.body);
```