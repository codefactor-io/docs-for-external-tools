Pattern: Inconsistent code format

Issue: -

## Description

Runs Prettier as an ESLint rule and reports differences.

## Options

* The first option:
  - Objects are passed directly to Prettier as [options](https://github.com/prettier/prettier#options). Example:
    
    ```json
    "prettier/prettier": ["error", {"singleQuote": true, "parser": "flow"}]
    ```

  - Or the string `"fb"` may be used to set "Facebook style" defaults:

    ```json
    "prettier/prettier": ["error", "fb"]
    ```

    Equivalent to:

    ```json
    "prettier/prettier": ["error", {
      "singleQuote": true,
      "trailingComma": "all",
      "bracketSpacing": false,
      "jsxBracketSameLine": true,
      "parser": "flow"
    }]
    ```

* The second option:

  - A string with a pragma that triggers this rule. By default, this rule applies to all files. However, if you set a pragma (this option), only files with that pragma in the heading docblock will be checked. All pragmas must start with `@`. Example:

    ```json
    "prettier/prettier": ["error", null, "@prettier"]
    ```

    Only files with `@prettier` in the heading docblock will be checked:

    ```js
    /** @prettier */

    console.log(1 + 2 + 3);
    ```

    Or:

    ```js
    /**
     * @prettier
     */

    console.log(4 + 5 + 6);
    ```

    _This option is useful if you're migrating a large codebase and already use pragmas like `@flow`._
