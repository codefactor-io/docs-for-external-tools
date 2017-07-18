Pattern: Single-line Javadoc comment should be multi-line

Issue: -

## Description

Checks that a Javadoc block can fit in a single line and doesn't contain at-clauses. Javadoc comment that contains at least one at-clause should be formatted in a few lines. 

## Examples

Default configuration: 


```xml
<module name="SingleLineJavadoc"/>
```
        

To specify a list of ignored at-clauses and make inline at-clauses not ignored: 


```xml
<module name="SingleLineJavadoc">
    <property name="ignoredTags" value="@inheritDoc, @see"/>
    <property name="ignoreInlineTags" value="false"/>
</module>
```

## Further Reading

* [checkstyle - SingleLineJavadoc](http://checkstyle.sourceforge.net/config_javadoc.html#SingleLineJavadoc)