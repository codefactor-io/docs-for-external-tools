Pattern: Leaked event listener

Issue: -

## Description

Enforces that every `addEventListener` in a component or custom Hook has a corresponding `removeEventListener`.

Adding an event listener without removing it can lead to memory leaks and unexpected behavior. This is because the event listener will continue to exist even after the component or hook is unmounted.

Examples of **incorrect** code for this rule:

```tsx
import React, { Component } from "react";

class MyComponent extends Component {
  componentDidMount() {
    document.addEventListener("click", this.handleClick);
    //                                 ^^^^^^^^^^^^^^^^
    //                                 - A 'addEventListener' in 'componentDidMount' should have a corresponding 'removeEventListener' in 'componentWillUnmount' method.
  }

  handleClick() {
    console.log("clicked");
  }

  render() {
    return null;
  }
}
```

Examples of **correct** code for this rule:

```html
import React, { Component } from "react";

class MyComponent extends Component {
  componentDidMount() {
    document.addEventListener("click", this.handleClick);
  }

  componentWillUnmount() {
    document.removeEventListener("click", this.handleClick);
  }

  handleClick() {
    console.log("clicked");
  }

  render() {
    return null;
  }
}
```
