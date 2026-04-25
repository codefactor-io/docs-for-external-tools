Pattern: Unassigned variable

Issue: -

## Description

This rule flags let or var declarations that are never assigned a value but are still read or used in the code. Since these variables will always be `undefined`, their usage is likely a programming mistake.

## Examples

Example of **incorrect** code:

```ts
let status;
if (status === "ready") {
  console.log("Ready!");
}
```

Example of **correct** code:

```ts
let message = "hello";
console.log(message);

let user;
user = getUser();
console.log(user.name);
```