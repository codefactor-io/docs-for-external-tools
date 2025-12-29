Pattern: Unnecessary alias in import

Issue: -

## Description

Detects unnecessary aliases in import use statements.

Aliasing something to the same name as the original construct is considered useless (though allowed in PHP). Note: as OO and function names in PHP are case-insensitive, aliasing to the same name, using a different case is also considered useless.

## Further Reading

* [Universal.UseStatements.NoUselessAliases](https://github.com/PHPCSStandards/PHPCSExtra?tab=readme-ov-file#universalusestatementsnouselessaliases-wrench-books)