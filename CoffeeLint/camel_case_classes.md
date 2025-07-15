Pattern: Invalid class name

Issue: -

## Description

This rule mandates that all class names are _UpperCamelCased_. Camel casing class names is a generally accepted way of distinguishing constructor functions - which require the `new` prefix to behave properly - from plain old functions.

## Examples

``` coffeescript
# Good!
class BoaConstrictor


# Bad!
class boaConstrictor
```

## Further Reading

* [CoffeeLint - camel_case_classes](https://coffeelint.github.io/#options)
* 
