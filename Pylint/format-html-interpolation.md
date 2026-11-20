Pattern: Interpolated format string passed to `format_html()`

Issue: -

## Description

Building the format string for `format_html()` or `format_html_join()` with an f-string, `str.format()`, `%` formatting, or concatenation inserts values before Django can escape them. Untrusted input can then become executable HTML, creating a cross-site scripting (XSS) vulnerability.

Keep the format string literal and pass dynamic values as separate arguments so Django can escape them.

## Examples

Example of **incorrect** code:

```python
from django.utils.html import format_html


def greeting(name):
    return format_html(f"<b>{name}</b>")
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
