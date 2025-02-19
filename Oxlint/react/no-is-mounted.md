Pattern: Use of `isMounted` method

Issue: -

## Description

The `isMounted` method is considered an anti-pattern and is not available in ES6 class components. It has been deprecated as it often indicates underlying issues in component lifecycle management.

## Examples

Example of **incorrect** code:
```jsx
class Hello extends React.Component {
  someMethod() {
    if (!this.isMounted()) {
      return;
    }
  }
  render() {
    return <div onClick={this.someMethod.bind(this)}>Hello</div>;
  }
}
```

Example of **correct** code:
```jsx
class Hello extends React.Component {
  _isMounted = false;
  
  componentDidMount() {
    this._isMounted = true;
  }
  
  componentWillUnmount() {
    this._isMounted = false;
  }
  
  someMethod() {
    if (!this._isMounted) {
      return;
    }
  }
}
```