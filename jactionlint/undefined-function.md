Pattern: Undefined function

Issue: -

## Description

An expression calls a function that GitHub Actions does not define. This is often caused by a misspelled function name.

Use a supported built-in function and check its spelling.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo "${{ startWith('hello', 'he') }}"
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
* [jactionlint - undefined-function](https://jactionlint.jdx.dev/rules#undefined-function)
