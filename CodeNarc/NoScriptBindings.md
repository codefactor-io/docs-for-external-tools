Pattern: Global variable bound to script

Issue: -

## Description

Reports occurrences of global variables that are bound to a script.

These should be avoided as concurrent executions can modify and read the shared variable, leading to concurrency bugs.

Example of violations:

```groovy
b = 1                       // violation
def myMethod() {
	a = 1                   // violation
}

// These are fields and local variables; they are OK
int b = 1
def myMethod2() {
	Integer a = 1
}
```
