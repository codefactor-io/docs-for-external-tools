Pattern: Missing `React` import with JSX usage

Issue: -

## Description

JSX syntax transpiles to `React.createElement()` calls, requiring the `React` variable to be in scope. Without importing React, JSX code will fail at runtime.

## Examples

Example of **incorrect** code:
```jsx
var a = <a />;
```

Example of **correct** code:
```jsx
import React from "react";
var a = <a />;
```