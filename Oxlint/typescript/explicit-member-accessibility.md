Pattern: Missing explicit member accessibility

Issue: -

## Description

TypeScript allows placing explicit `public`, `protected`, and `private`
accessibility modifiers in front of class members. The modifiers exist
solely in the type system and serve to describe who is allowed to access
those members.

Leaving off accessibility modifiers makes for less code to read and
write. Members are `public` by default. However, adding explicit
modifiers can make code more readable and explicit about who can use
which properties.

## Examples

### `{ "accessibility": "explicit" }` (default)

Example of **incorrect** code:
```ts
class Animal {
  constructor(name: string) {}
  animalName: string;
  get name(): string {
    return this.animalName;
  }
}
```

Example of **correct** code:
```ts
class Animal {
  public constructor(name: string) {}
  private animalName: string;
  public get name(): string {
    return this.animalName;
  }
}
```

### `{ "accessibility": "no-public" }`

Example of **incorrect** code:
```ts
class Animal {
  public constructor(
    public breed: string,
    name: string,
  ) {}
  public animalName: string;
  public get name(): string {
    return this.animalName;
  }
}
```

Example of **correct** code:
```ts
class Animal {
  constructor(
    protected breed: string,
    name: string,
  ) {}
  private animalName: string;
  get name(): string {
    return this.animalName;
  }
}
```

### `{ "overrides": { "constructors": "no-public" } }`

Disallow the use of `public` on constructors while requiring explicit
modifiers everywhere else.

Example of **incorrect** code:
```ts
class Animal {
  public constructor(protected animalName: string) {}
}
```

Example of **correct** code:
```ts
class Animal {
  constructor(protected animalName: string) {}
  public get name(): string {
    return this.animalName;
  }
}
```

### `{ "accessibility": "no-public", "overrides": { "properties": "explicit" } }`

Require explicit modifiers on properties while disallowing `public`
everywhere else.

Example of **incorrect** code:
```ts
class Animal {
  legs: number;
  private hasFleas: boolean;
}
```

Example of **correct** code:
```ts
class Animal {
  public legs: number;
  private hasFleas: boolean;
}
```
