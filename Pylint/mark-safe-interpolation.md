Pattern: Interpolated string passed to `mark_safe()`

Issue: -

## Description

`mark_safe()` marks a string as safe HTML without escaping its contents. Applying it to a string containing untrusted values can let those values inject HTML or JavaScript, creating a cross-site scripting (XSS) vulnerability.

Use `format_html()` with a literal format string and separate arguments so Django can escape the dynamic values.

## Examples

Example of **incorrect** code:

```python
from django.utils.safestring import mark_safe


def greeting(name):
    return mark_safe(f"<b>{name}</b>")
```

Example of **correct** code:

```python
from django.utils.html import format_html


def greeting(name):
    return format_html("<b>{}</b>", name)
```

## Further Reading

* [pylint-django - HTML interpolation checker](https://github.com/pylint-dev/pylint-django/blob/master/pylint_django/checkers/format_html.py)
* [Django - format_html()](https://docs.djangoproject.com/en/stable/ref/utils/#django.utils.html.format_html)
