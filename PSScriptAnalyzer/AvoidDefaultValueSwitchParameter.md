Pattern: Use of default value switch parameter as `$True`

Issue: -

## Description

Switch parameters for commands should default to false.

## How

Change the default value of the switch parameter to be false.

Example of **incorrect** code:

``` PowerShell
function Test-Script
{
    [CmdletBinding()]
    Param
    (
        [String]
        $Param1,

        [switch]
        $Switch=$True
    )
    ...
}
```

Example of **correct** code:

``` PowerShell
function Test-Script
{
    [CmdletBinding()]
    Param
    (
        [String]
        $Param1,

        [switch]
        $Switch=$False
    )
    ...
}
```

## Further Reading

* [PSScriptAnalyzer - AvoidDefaultValueSwitchParameter](https://github.com/PowerShell/PSScriptAnalyzer/tree/master/docs/Rules/AvoidDefaultValueSwitchParameter.md)
