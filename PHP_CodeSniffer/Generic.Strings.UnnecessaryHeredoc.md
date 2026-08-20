Pattern: Unnecessary heredoc syntax

Issue: -

## Description

Detects heredoc strings that do not contain interpolation or expressions. Use nowdoc syntax for these strings instead.

## Example

Example of **incorrect** code:

```php
$message = <<<TEXT
Hello, world!
TEXT;
```

Example of **correct** code:

```php
$message = <<<'TEXT'
Hello, world!
TEXT;
```

## Further Reading

* [PHP_CodeSniffer - Generic.Strings.UnnecessaryHeredoc](https://github.com/PHPCSStandards/PHP_CodeSniffer/blob/4.x/src/Standards/Generic/Sniffs/Strings/UnnecessaryHeredocSniff.php)
* [PHP_CodeSniffer issue #1320](https://github.com/PHPCSStandards/PHP_CodeSniffer/issues/1320)
