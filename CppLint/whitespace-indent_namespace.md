Pattern: Indentation winthin a namespace

Issue: -

## Description

Do not indent within a namespace.


```cpp
// In the .h file
namespace Test {

// All declarations are within the namespace scope.
// Notice the lack of indentation.
class MyClass {
 public:
  ...
  void Foo();
};

}  // namespace Test
```


## Further Reading

* [Google C++ Style Guide - Namespaces](https://google.github.io/styleguide/cppguide.html#Namespaces)