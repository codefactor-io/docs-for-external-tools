Pattern: Interpolated format string passed to format_html

Issue: -

## Description

Used when the format string of format_html()/format_html_join() is built with an f-string, str.format(), %-formatting or + concatenation, which bypasses escaping. See https://code.djangoproject.com/ticket/34609

Example of **incorrect** code:

```python
from django.utils.html import format_html


def greeting(name):
    return format_html(f"<b>{name}</b>")  # [format-html-interpolation]
```

Example of **correct** code:

```python
from django.utils.html import format_html


def greeting(name):
    return format_html("<b>{}</b>", name)
```
