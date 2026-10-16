Pattern: Webshell detected

Issue: -

## Description

A file matches a webshell signature from the bundled YARA rules: PHP `eval`/`assert`/`system` on request input, `eval(base64_decode(...))`-style obfuscation, known shell families (c99, r57, WSO, b374k, weevely, China Chopper, Godzilla, Behinder), or Python, JSP and ASPX request-to-exec patterns. The message names the matching YARA rule.


Example of **insecure** code:

```php
<?php eval($_POST['cmd']); ?>
```

## Further Reading

* [YARA documentation](https://yara.readthedocs.io/)
* [Neo23x0 signature-base](https://github.com/Neo23x0/signature-base)
