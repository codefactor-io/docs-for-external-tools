Pattern: Component-level state management with `setState`

Issue: -

## Description

When using state management architectures like Flux or Redux, local component state becomes an anti-pattern. Using `setState` in components can make state changes harder to track and maintain, especially in read-only applications that don't require forms.

## Examples

Example of **incorrect** code:
```jsx
var Hello = createReactClass({
  handleClick: function() {
    this.setState({
      name: this.props.name.toUpperCase()
    });
  },
  render: function() {
    return <div onClick={this.handleClick.bind(this)}>Hello {this.state.name}</div>;
  }
});
```

Example of **correct** code:
```jsx
var Hello = createReactClass({
  render: function() {
    return <div onClick={this.props.onClickHandler}>Hello {this.props.name}</div>;
  }
});
```