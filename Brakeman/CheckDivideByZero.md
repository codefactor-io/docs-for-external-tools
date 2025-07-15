Pattern: Division by zero

Issue: -
 
## Description

Integer division by zero (`0`) in Ruby results in a `ZeroDivisionError` exception.

While not strictly a security issue, if an attacker can trigger a large number of exceptions it can harm site availability.

Brakeman warns when it finds potential division by zero with integers. Dividing a float by zero or `0.0` in Ruby results in `Infinity`, not an exception.

## Further Reading

* [Brakeman - Divide By Zero](https://brakemanscanner.org/docs/warning_types/divide_by_zero/)
