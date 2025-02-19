Pattern: Use of `createReactClass` instead of ES6 class

Issue: -

## Description

ES6 classes provide a more modern and standardized way to create React components compared to the legacy `createReactClass` method. Using ES6 classes improves code consistency and takes advantage of JavaScript's built-in class features.

## Examples

Example of **incorrect** code:
```jsx
var Hello = createReactClass({
  render: function() {
    return <div>Hello {this.props.name}</div>;
  }
});
```

Example of **correct** code:
```jsx
class Hello extends React.Component {
  render() {
    return <div>Hello {this.props.name}</div>;
  }
}
```