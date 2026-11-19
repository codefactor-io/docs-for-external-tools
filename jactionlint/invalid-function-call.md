Pattern: Invalid function call

Issue: -

## Description

A built-in expression function receives the wrong number or types of arguments. For example, `startsWith` expects two strings.

Check the function's signature and pass compatible arguments.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo "${{ startsWith('hello') }}"
      - run: echo "${{ startsWith('hello', github.event) }}"
```

Example of **correct** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo "${{ startsWith('hello', 'he') }}"
```

## Further Reading

* [jactionlint - Contexts and built-in functions](https://jactionlint.jdx.dev/checks#check-contexts-and-builtin-func)
* [jactionlint - invalid-function-call](https://jactionlint.jdx.dev/rules#invalid-function-call)
