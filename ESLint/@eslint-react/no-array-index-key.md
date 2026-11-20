Pattern: Use of array index as key

Issue: -

## Description

An array index describes an item's position, not its identity. Using it as a React `key` can associate state with the wrong item when the list is reordered or items are inserted or removed.

Use a stable identifier from the data instead. Converting the index to a string or adding a prefix does not make it stable.

## Examples

Example of **incorrect** code:

```jsx
function ItemList({ items }) {
  return (
    <ul>
      {items.map((item, index) => (
        <li key={index}>{item.name}</li>
      ))}
    </ul>
  );
}
```

Example of **correct** code:

```jsx
function ItemList({ items }) {
  return (
    <ul>
      {items.map((item) => (
        <li key={item.id}>{item.name}</li>
      ))}
    </ul>
  );
}
```

## Further Reading

* [ESLint React - no-array-index-key](https://eslint-react.xyz/docs/rules/no-array-index-key)
