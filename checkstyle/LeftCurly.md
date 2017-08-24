Pattern: Wrong `{` placement

Issue: -

## Description

Checks for the placement of left curly braces (`'{'`) for code blocks. The policy to verify is specified using the property `option`. Policies `eol` and `nlow` take into account the property `maxLineLength`. 

## Examples

To configure the check: 


```xml
<module name="LeftCurly"/>
```
        

To configure the check to apply the `nl` policy to type blocks: 


```xml
<module name="LeftCurly">
    <property name="option" value="nl"/>
    <property name="tokens" value="CLASS_DEF,INTERFACE_DEF"/>
</module>
```
        

An example of how to configure the check to validate `enum` definitions: 


```xml
<module name="LeftCurly">
    <property name="ignoreEnums" value="false"/>
</module>
```

## Further Reading

* [checkstyle - Lcurly property](http://checkstyle.sourceforge.net/property_types.html#lcurly)
* [checkstyle - LeftCurly](http://checkstyle.sourceforge.net/config_blocks.html#LeftCurly)