Pattern: Use of curly brace syntax for namespace declaration

Issue: -

## Description

Disallows namespace declarations that use curly braces. Namespace declarations must use the semicolon syntax instead.

Example of **incorrect** code:

```php
namespace App\Domain {
    class User {}
}
```

Example of **correct** code:

```php
namespace App\Domain;

class User {}
```

## Further Reading

* [Universal.Namespaces.DisallowCurlyBraceSyntax](https://github.com/PHPCSStandards/PHPCSExtra?tab=readme-ov-file#universalnamespacesdisallowcurlybracesyntax-bar_chart-books)
