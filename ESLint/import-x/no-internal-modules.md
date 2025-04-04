Pattern: Internal module import

Issue: -

## Description

This rule prevents importing the submodules of other modules. It helps enforce a consistent pattern for importing modules and avoiding reaching into internal implementation details of other modules.

The rule has two mutually exclusive options that are arrays of minimatch/glob patterns:
- `allow` - includes paths and import statements that can be imported with reaching
- `forbid` - excludes paths and import statements that can be imported with reaching

## Examples

Given the following folder structure:
```
my-project
├── actions
│   └── getUser.js
│   └── updateUser.js
├── reducer
│   └── index.js
│   └── user.js
├── redux
│   └── index.js
│   └── configureStore.js
└── app
│   └── index.js
│   └── settings.js
└── entry.js
```

Example of **incorrect** code with `{ "allow": [ "**/actions/*", "source-map-support/*" ] }`:
```js
/**
 *  in my-project/entry.js
 */
import { settings } from './app/index' // Reaching to "./app/index" is not allowed
import userReducer from './reducer/user' // Reaching to "./reducer/user" is not allowed
import configureStore from './redux/configureStore' // Reaching to "./redux/configureStore" is not allowed

export { settings } from './app/index' // Reaching to "./app/index" is not allowed
export * from './reducer/user' // Reaching to "./reducer/user" is not allowed
```

Example of **correct** code with `{ "allow": [ "**/actions/*", "source-map-support/*" ] }`:
```js
/**
 *  in my-project/entry.js
 */
import 'source-map-support/register'
import { settings } from '../app'
import getUser from '../actions/getUser'

export * from 'source-map-support/register'
export { settings } from '../app'
```

Example of **incorrect** code with `{ "forbid": [ "**/actions/*", "source-map-support/*" ] }`:
```js
/**
 *  in my-project/entry.js
 */
import 'source-map-support/register'
import getUser from '../actions/getUser'

export * from 'source-map-support/register'
export getUser from '../actions/getUser'
```

Example of **correct** code with `{ "forbid": [ "**/actions/*", "source-map-support/*" ] }`:
```js
/**
 *  in my-project/entry.js
 */
import 'source-map-support'
import { getUser } from '../actions'

export * from 'source-map-support'
export { getUser } from '../actions'
```