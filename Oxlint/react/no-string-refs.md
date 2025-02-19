Pattern: String literal in React `ref` attribute

Issue: -

## Description

Using string literals in `ref` attributes is a legacy approach that has been deprecated in React. Callback refs or the `createRef` API provide better typechecking and allow refs to work in concurrent mode.

## Examples

Example of **incorrect** code:
```jsx
var Hello = createReactClass({
  render: function() {
    return <div ref="hello">Hello, world.</div>;
  }
});

var Hello = createReactClass({
  componentDidMount: function() {
    var component = this.refs.hello;
    // ...do something with component
  }
});
```

Example of **correct** code:
```jsx
var Hello = createReactClass({
  componentDidMount: function() {
    var component = this.hello;
  },
  render() {
    return <div ref={(c) => { this.hello = c; }}>Hello, world.</div>;
  }
});
```