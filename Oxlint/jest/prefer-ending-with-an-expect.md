Pattern: Test does not end with assertion

Issue: -

## Description

A test that doesn't end with an assertion may be performing side effects or setup after its last check, which makes the test harder to understand and can hide failures. Ending with an assertion ensures the test's final action is verifying behavior.

## Examples

Example of **incorrect** code:

```ts
it("lets me change the selected option", () => {
  const container = render(MySelect, {
    props: { options: [1, 2, 3], selected: 1 },
  });

  expect(container).toBeDefined();
  expect(container.toHTML()).toContain('<option value="1" selected>');

  container.setProp("selected", 2);
});
```

Example of **correct** code:

```ts
it("lets me change the selected option", () => {
  const container = render(MySelect, {
    props: { options: [1, 2, 3], selected: 1 },
  });

  expect(container).toBeDefined();
  expect(container.toHTML()).toContain('<option value="1" selected>');

  container.setProp("selected", 2);

  expect(container.toHTML()).not.toContain('<option value="1" selected>');
  expect(container.toHTML()).toContain('<option value="2" selected>');
});
```