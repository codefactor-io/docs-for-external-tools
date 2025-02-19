Pattern: Webpack loader syntax in import

Issue: -

## Description

Using Webpack loader syntax directly in import statements couples the code to Webpack. Loader configuration should be specified in the Webpack configuration file instead of the import statement.

## Examples

Example of **incorrect** code:
```javascript
import myModule from "my-loader!my-module";
import theme from "style!css!./theme.css";
```

Example of **correct** code:
```javascript
import myModule from "./my-module";
import theme from "./theme.css";
```