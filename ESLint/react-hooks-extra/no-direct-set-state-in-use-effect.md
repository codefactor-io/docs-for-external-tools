Pattern: Direct call to `set` function of `useState` in `useEffect`

Issue: -

## Description

Disallows direct calls to the `set` function of `useState` in `useEffect`.

This rule only checks for direct calls to the `set` function of `useState` in `useEffect`. It does not check for calls to `set` function in callbacks, event handlers, or `Promise.then` functions.


Example of **incorrect** code:

```js
import { useEffect, useState } from "react";
 
function Form() {
  const [firstName, setFirstName] = useState("Taylor");
  const [lastName, setLastName] = useState("Swift");
 
  // 🔴 Avoid: redundant state and unnecessary Effect
  const [fullName, setFullName] = useState("");
  useEffect(() => {
    setFullName(firstName + " " + lastName);
  }, [firstName, lastName]);
  // ...
}
```

Example of **correct** code:

```js
import { useState } from "react";
 
function Form() {
  const [firstName, setFirstName] = useState("Taylor");
  const [lastName, setLastName] = useState("Swift");
  // ✅ Good: calculated during rendering
  const fullName = firstName + " " + lastName;
  // ...
}
```

## Further Reading

* [GitHub - no-direct-set-state-in-use-effect](https://eslint-react.xyz/docs/rules/hooks-extra-no-direct-set-state-in-use-effect)