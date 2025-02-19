Pattern: Missing `key` prop in array element

Issue: -

## Description

React requires a unique `key` prop for elements within arrays to efficiently track changes and handle updates. Without keys, React cannot identify which items have changed, been added, or been removed.

## Examples

Example of **incorrect** code:
```jsx
[1, 2, 3].map((x) => <App />);
[1, 2, 3]?.map((x) => <BabelEslintApp />);
```

Example of **correct** code:
```jsx
[1, 2, 3].map((x) => <App key={x} />);
[1, 2, 3]?.map((x) => <BabelEslintApp key={x} />);
```