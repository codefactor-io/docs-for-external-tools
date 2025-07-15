Pattern: Use of global variable

Issue: -

## Description

Global variables are strongly discouraged as they can cause errors across different systems.

Globally scoped variables include:
* Automatic variables
* Preference variables
* Variables, aliases, and functions that are in your Windows PowerShell profiles

To understand more about scoping, see `Get-Help about_Scopes`.

## How

Use other scope modifiers for variables.

Example of **incorrect** code:

``` PowerShell
$Global:var1 = $null
function Test-NotGlobal ($var)
{
	$a = $var + $var1
}
```

Example of **correct** code:

``` PowerShell
$var1 = $null
function Test-NotGlobal ($var1, $var2)
{
		$a = $var1 + $var2
}
```

## Further Reading

* [PSScriptAnalyzer - AvoidGlobalVars](https://github.com/PowerShell/PSScriptAnalyzer/tree/master/docs/Rules/AvoidGlobalVars.md)
