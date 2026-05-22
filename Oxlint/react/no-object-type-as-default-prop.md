Pattern: Fresh references in default props

Issue: -

## Description

Default values of destructured parameters are evaluated on every render. When the default is an object literal, array literal, function expression, class expression, regular expression, `new` expression, or JSX element, a new reference is created on every render. Passing that fresh reference to child components or hook dependency arrays defeats memoization and causes unnecessary re-renders.

Note: you do not need to enable this rule when using React Compiler, since React Compiler memoizes default values automatically.

## Examples

Example of **incorrect** code:

```ts
function Foo({ items = [] }) {
  return <List items={items} />;
}

const Bar = ({ config = {} }) => <div data-config={config} />;

function Baz({ onClick = () => {} }) {
  return <button onClick={onClick} />;
}
```

Example of **correct** code:

```ts
const DEFAULT_ITEMS = [];
function Foo({ items = DEFAULT_ITEMS }) {
  return <List items={items} />;
}

const Bar = ({ name = "world" }) => <div>{name}</div>;

function Baz({ onClick }) {
  return <button onClick={onClick} />;
}
```