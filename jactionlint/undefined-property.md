Pattern: Undefined property

Issue: -

## Description

An undefined variable or property is accessed in an expression.

The rules `undefined-property`, `undefined-function` and `invalid-function-call` (all in the `correctness` profile) report a context or property that does not exist, a function that does not exist, and a call of a built-in function with the wrong number or types of arguments.

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      # Access undefined context
      - run: echo '${{ unknown_context }}'
      # Access undefined property of context
      - run: echo '${{ github.events }}'
      # Calling undefined function (start's'With is correct)
      - run: echo "${{ startWith('hello, world', 'lo,') }}"
      # Wrong number of arguments
      - run: echo "${{ startsWith('hello, world') }}"
      # Wrong type of parameter
      - run: echo "${{ startsWith('hello, world', github.event) }}"
      # Function overloads can be handled properly. contains() has string version and array version
      - run: echo "${{ contains('hello, world', 'lo,') }}"
      - run: echo "${{ contains(github.event.issue.labels.*.name, 'enhancement') }}"
```

## Further Reading

* [jactionlint - Contexts and built-in functions](https://jactionlint.jdx.dev/checks#check-contexts-and-builtin-func)
* [jactionlint - undefined-property](https://jactionlint.jdx.dev/rules#undefined-property)
