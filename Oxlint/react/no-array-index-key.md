Pattern: Array index as React `key` prop

Issue: -

## Description

Using array indices as React keys can lead to incorrect component behavior when items are reordered or deleted. Keys should uniquely identify list items across re-renders, while array indices change based on item position.

## Examples

Example of **incorrect** code:
```jsx
things.map((thing, index) => <Hello key={index} />);
```

Example of **correct** code:
```jsx
things.map((thing, index) => <Hello key={thing.id} />);
```