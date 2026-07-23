Pattern: Multiple namespace declarations in file

Issue: -

## Description

Disallows more than one namespace declaration in a file.

Example of **incorrect** code:

```php
namespace App\Domain;

class User {}

namespace App\Http;

class UserController {}
```

Example of **correct** code:

```php
namespace App\Domain;

class User {}
```

## Further Reading

* [Universal.Namespaces.OneDeclarationPerFile](https://github.com/PHPCSStandards/PHPCSExtra?tab=readme-ov-file#universalnamespacesonedeclarationperfile-books)
