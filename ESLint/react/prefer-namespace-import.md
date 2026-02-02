Pattern: Missing React namespace import

Issue: -

## Description

Enforces importing React via a namespace import.

Examples of **incorrect** code for this rule:

```js
import React from "react";

import type React from "react";

import React, { useState } from "react";

import type React, { useState } from "react";
```

Examples of **correct** code for this rule:


```js
import * as React from "react";

import type * as React from "react";

import { useState } from "react";

import type { useState } from "react";
```