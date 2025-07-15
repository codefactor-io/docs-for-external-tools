Pattern: Invoking empty member

Issue: -

## Description

Invoking non-constant members can cause potential bugs. Please double check the syntax to make sure that invoked members are constants.

## How

Provide the requested members for a given type or class.

Example of **incorrect** code:

``` PowerShell
$MyString = "abc"
$MyString.('len'+'gth')
```

Example of **correct** code:

``` PowerShell
$MyString = "abc"
$MyString.('length')
```

## Further Reading

* [PSScriptAnalyzer - AvoidInvokingEmptyMembers](https://github.com/PowerShell/PSScriptAnalyzer/tree/master/docs/Rules/AvoidInvokingEmptyMembers.md)
