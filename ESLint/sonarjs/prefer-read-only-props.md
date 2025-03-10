Pattern: Missing use of read-only prop

Issue: -

## Description

React props should be read-only because it helps to enforce the principle of immutability in React functional components. By making props read-only, you ensure that the data passed from a parent component to a child component cannot be modified directly by the child component. This helps maintain a clear data flow and prevents unexpected side effects.

Overall, enforcing read-only props in React helps improve code reliability, maintainability, and performance.

Example of **incorrect** code:

```ts
interface Props {
  name: string;
}

function Welcome(props: Props) { // Noncompliant: The component props are not read-only
  return <div>Hello {props.name}</div>;
}
```

Example of **correct** code:

```ts
interface Props {
  name: string;
}

function Welcome(props: Readonly<Props>) {
  return <div>Hello {props.name}</div>;
}
```

## Further Reading

* [prefer-read-only-props](https://sonarsource.github.io/rspec/#/rspec/S6759/javascript)