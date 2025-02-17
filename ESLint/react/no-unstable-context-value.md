Pattern: Unstable value for `Context.Provider`

Issue: -

## Description

React Context, and all its child nodes and Consumers are rerendered whenever the value prop changes. Because each Javascript object carries its own identity, things like object expressions (`{foo: 'bar'}`) or function expressions get a new identity on every run through the component. This makes the context think it has gotten a new object and can cause needless rerenders and unintended consequences.

This can be a pretty large performance hit because not only will it cause the context providers and consumers to rerender with all the elements in its subtree, the processing for the tree scan react does to render the provider and find consumers is also wasted.

Examples of **incorrect** code for this rule:

```js
import React from "react";
 
const MyContext = React.createContext({});
 
function MyComponentProvider() {
  return (
    <MyContext.Provider value={{ foo: "bar" }}>
      {/*                      ^^^^^^^^^^^^^^ */}
      {/*                      - A/an 'Object literal' passed as the value prop to the context provider should not be constructed. It will change on every render. Consider wrapping it in a useMemo hook */}
      <ExampleConsumer />
    </MyContext.Provider>
  );
}
```

Examples of **correct** code for this rule:

```js
import React, { useMemo } from "react";
 
const MyContext = React.createContext({});
 
const value = { foo: "bar" };
 
function MyComponentProvider() {
  return (
    <MyContext.Provider value={value}>
      <ExampleConsumer />
    </MyContext.Provider>
  );
}
```