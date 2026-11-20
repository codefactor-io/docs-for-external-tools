Pattern: Interpolated string passed to mark_safe

Issue: -

## Description

Used when mark_safe() is called on a string built with an f-string, str.format(), %-formatting or + concatenation, which is not escaped at all. See https://docs.djangoproject.com/en/stable/ref/utils/#django.utils.html.format_html

Example of **incorrect** code:

```python
from django.utils.safestring import mark_safe


def greeting(name):
    return mark_safe(f"<b>{name}</b>")  # [mark-safe-interpolation]
```

Example of **correct** code:

```python
from django.utils.html import format_html


def greeting(name):
    return format_html("<b>{}</b>", name)
```
