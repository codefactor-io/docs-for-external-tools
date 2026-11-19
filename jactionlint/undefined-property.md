Pattern: Undefined property

Issue: -

## Description

An expression refers to a context, variable, or property that is not defined. This is often caused by a misspelled name, such as `github.events` instead of `github.event`.

Check the name and use a property available in that context.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo '${{ github.events }}'
```

Example of **correct** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo '${{ github.event_name }}'
```

## Further Reading

* [jactionlint - Contexts and built-in functions](https://jactionlint.jdx.dev/checks#check-contexts-and-builtin-func)
* [jactionlint - undefined-property](https://jactionlint.jdx.dev/rules#undefined-property)
