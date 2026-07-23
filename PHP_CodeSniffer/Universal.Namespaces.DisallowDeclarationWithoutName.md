Pattern: Namespace declaration without a name

Issue: -

## Description

Disallows namespace declarations without a namespace name. This rule only applies to declarations that use the curly brace syntax.

Example of **incorrect** code:

```php
namespace {
    function helper() {}
}
```

Example of **correct** code:

```php
namespace App\Helpers {
    function helper() {}
}
```

## Further Reading

* [Universal.Namespaces.DisallowDeclarationWithoutName](https://github.com/PHPCSStandards/PHPCSExtra?tab=readme-ov-file#universalnamespacesdisallowdeclarationwithoutname-bar_chart-books)
