Pattern: Use of `findDOMNode`

Issue: -

## Description

`findDOMNode` is a legacy escape hatch that breaks component encapsulation by accessing the underlying DOM node. It has been deprecated in `StrictMode` and should be avoided in favor of refs and other React-provided methods.

## Examples

Example of **incorrect** code:
```jsx
class MyComponent extends Component {
  componentDidMount() {
    findDOMNode(this).scrollIntoView();
  }
  render() {
    return <div />;
  }
}
```

Example of **correct** code:
```jsx
class MyComponent extends Component {
  componentDidMount() {
    this.divRef.current.scrollIntoView();
  }
  render() {
    return <div ref={this.divRef} />;
  }
}
```