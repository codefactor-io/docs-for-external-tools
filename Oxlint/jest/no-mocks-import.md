Pattern: Direct mock import

Issue: -

## Description

Importing directly from `__mocks__` directory can lead to unexpected behavior. Jest's automatic mock handling should be used instead.

## Examples

Example of **incorrect** code:
```javascript
import mock from "./__mocks__/service";
const helper = require("./__mocks__/helper");
```

Example of **correct** code:
```javascript
import service from "./service";
const helper = require("./helper");

jest.mock("./service");
jest.mock("./helper");
```