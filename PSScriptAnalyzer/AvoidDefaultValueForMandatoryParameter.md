Pattern: Use of default value for mandatory parameter

Issue: -

## Description

Mandatory parameters should not have a default values because there is no scenario where the default can be used because `PowerShell` will prompt anyway if the parameter value is not specified when calling the function.

Example of **incorrect** code:

``` PowerShell
function Test
{

    [CmdletBinding()]
    Param
    (
        [Parameter(Mandatory=$true)]
        $Parameter1 = 'default Value'
    )
}
```

Example of **correct** code:

``` PowerShell
function Test
{
    [CmdletBinding()]
    Param
    (
        [Parameter(Mandatory=$true)]
        $Parameter1
    )
}
```

## Further Reading

* [PSScriptAnalyzer - AvoidDefaultValueForMandatoryParameter](https://github.com/PowerShell/PSScriptAnalyzer/tree/master/docs/Rules/AvoidDefaultValueForMandatoryParameter.md)
