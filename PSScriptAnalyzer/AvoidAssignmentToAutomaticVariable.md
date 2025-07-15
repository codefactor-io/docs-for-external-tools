Pattern: Assignment to automatic variable

Issue: -

## Description

`PowerShell` exposes some of its built-in variables that are known as automatic variables. Many of them are read-only and PowerShell would throw an error when trying to assign an value on those. Other automatic variables should only be assigned to in certain special cases to achieve a certain effect as a special technique.

To understand more about automatic variables, see `Get-Help about_Automatic_Variables`.

## How

Use variable names in functions or their parameters that do not conflict with automatic variables.

Example of **incorrect** code:

``` PowerShell
function Get-CustomErrorMessage($ErrorMessage){ $Error = "Error occurred: $ErrorMessage" }
```

The variable `$Error` is an automatic variables that exists in the global scope and should therefore never be used as a variable or parameter name.

Example of **correct** code:

``` PowerShell
function Get-CustomErrorMessage($ErrorMessage){ $FinalErrorMessage = "Error occurred: $ErrorMessage" }
```

## Further Reading

* [PSScriptAnalyzer - AvoidAssignmentToAutomaticVariable](https://github.com/PowerShell/PSScriptAnalyzer/tree/master/docs/Rules/AvoidAssignmentToAutomaticVariable.md)
