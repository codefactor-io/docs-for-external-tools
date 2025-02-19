Pattern: Direct mutation of `this.state`

Issue: -

## Description

Directly modifying `this.state` bypasses React's state management and can lead to state inconsistencies. Any direct mutations may be lost when `setState()` is called. Always use `setState()` to update state values.

## Examples

Example of **incorrect** code:
```jsx
var Hello = createReactClass({
  componentDidMount: function() {
    this.state.name = this.props.name.toUpperCase();
  }
});

class Hello extends React.Component {
  constructor(props) {
    super(props)
    doSomethingAsync(() => {
      this.state = 'bad';
    });
  }
}
```

Example of **correct** code:
```jsx
var Hello = createReactClass({
  componentDidMount: function() {
    this.setState({
      name: this.props.name.toUpperCase()
    });
  }
});

class Hello extends React.Component {
  constructor(props) {
    super(props)
    this.state = {
      foo: 'bar'
    }
  }
}
```