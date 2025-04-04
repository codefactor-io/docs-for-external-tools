Pattern: Webpack loader syntax in import

Issue: -

## Description

This rule forbids Webpack loader syntax in imports. Webpack allows specifying the loaders to use in the import source string using a special syntax like this:

```js
var moduleWithOneLoader = require('my-loader!./my-awesome-module')
```

This syntax is non-standard, so it couples the code to Webpack. The recommended way to specify Webpack loader configuration is in a Webpack configuration file.

## Examples

Example of **incorrect** code:
```js
import myModule from 'my-loader!my-module'
import theme from 'style!css!./theme.css'

var myModule = require('my-loader!./my-module')
var theme = require('style!css!./theme.css')
```

Example of **correct** code:
```js
import myModule from 'my-module'
import theme from './theme.css'

var myModule = require('my-module')
var theme = require('./theme.css')
```