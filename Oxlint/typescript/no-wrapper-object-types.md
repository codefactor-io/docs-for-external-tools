Pattern: Use of wrapper object types

Issue: -

## Description

Using wrapper object types (`String`, `Number`, `Boolean`, etc.) instead of their primitive counterparts (`string`, `number`, `boolean`) can lead to unexpected behavior and is not recommended in TypeScript.

## Examples

Example of **incorrect** code:
```ts
let myBoolean: Boolean;
let myNumber: Number;
let myString: String;
let mySymbol: Symbol;
let myBigInt: BigInt;
```

Example of **correct** code:
```ts
let myBoolean: boolean;
let myNumber: number;
let myString: string;
let mySymbol: symbol;
let myBigInt: bigint;
```