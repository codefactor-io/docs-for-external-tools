Pattern: Children passed as prop instead of nested content

Issue: -

## Description

React components should receive children through nested content between opening and closing tags, not as a prop. Using the children prop creates unnecessary complexity and can lead to confusion about the component's structure.

## Examples

Example of **incorrect** code:
```jsx
<div children='Children' />
<MyComponent children={<AnotherComponent />} />
<MyComponent children={['Child 1', 'Child 2']} />
React.createElement("div", { children: 'Children' })
```

Example of **correct** code:
```jsx
<div>Children</div>
<MyComponent>
  <span>Child 1</span>
  <span>Child 2</span>
</MyComponent>
React.createElement("div", {}, 'Children')
```