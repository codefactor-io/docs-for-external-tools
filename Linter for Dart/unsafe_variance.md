Pattern: Unsafe variance

Issue: -

## Description

 An instance variable whose type contains a type parameter of the enclosing class, mixin, or enum in a non-covariant position is likely to cause run-time failures due to failing type checks. For example, in `class C<X> {...}`, an instance variable of the form `void Function(X) myVariable;` may cause this kind of run-time failure.

The same is true for a getter or method whose return type has a non-covariant occurrence of a type parameter of the enclosing declaration. 

Example of **incorrect** code:

```dart
class C<X> {
  final bool Function(X) fun; // LINT
  C(this.fun);
}

void main() {
  C<num> c = C<int>((i) => i.isEven);
  c.fun(10); // Throws.
}
```

The problem is that `X` occurs as a parameter type in the type of `fun`.

One way to reduce the potential for run-time type errors is to ensure that the non-covariant member `fun` is only used on this. We cannot strictly enforce this, but we can make it private and add a forwarding method `fun` such that we can check locally in the same library that this constraint is satisfied: 

```dart
class C<X> {
  // ignore: unsafe_variance
  final bool Function(X) _fun;
  bool fun(X x) => _fun(x);
  C(this._fun);
}

void main() {
  C<num> c = C<int>((i) => i.isEven);
  c.fun(10); // Succeeds.
}
```

A fully safe approach requires a feature that Dart does not yet have, namely statically checked variance. With that, we could specify that the type parameter `X` is invariant (inout `X`).

It is possible to emulate invariance without support for statically checked variance. This puts some restrictions on the creation of subtypes, but faithfully provides the typing that `inout` would give: 

```dart
typedef Inv<X> = X Function(X);
typedef C<X> = _C<X, Inv<X>>;

class _C<X, Invariance extends Inv<X>> {
  // ignore: unsafe_variance
  final bool Function(X) fun; // Safe!
  _C(this.fun);
}

void main() {
  C<int> c = C<int>((i) => i.isEven);
  c.fun(10); // Succeeds.
}
```

## Further Reading

* [Linter for Dart - unsafe_variance](https://dart.dev/tools/linter-rules/unsafe_variance)