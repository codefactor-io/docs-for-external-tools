Pattern: Non-component React export

Issue: -

## Description

Fast Refresh can only reliably retain state if a module exports components and avoids patterns that confuse the refresh runtime. Problematic patterns (like `export *`, anonymous default functions, exporting arrays of JSX, or mixing non-component exports in unsupported ways) can cause:

    Components to remount and lose state on edit
    Missed updates (no refresh) or overly broad reloads
    Fragile HMR behavior that differs between bundlers

By enforcing predictable exports, edits stay fast and stateful during development.

## Examples

Example of **incorrect** code:

```jsx
// 1) Mixing util exports with components in unsupported ways
export const foo = () => {}; // util, not a component
export const Bar = () => <></>; // component
```

Example of **correct** code:

```jsx
// Named or default component exports are fine
export default function Foo() {
  return null;
}
```