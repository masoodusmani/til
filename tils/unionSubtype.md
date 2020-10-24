---
title: Subtype union types with full intellisense with a type function
date: 2020-10-24
tags:
  - typescript
  - javascript
  - types
layout: layouts/post.njk
---

If you want to create a subtype of a union type, but want intellisense and type checking to work both while creating the type and while using it, you'll need to create a type function:

```ts
type Extends<T, U extends T> = U
```

Object keys are a union type. You might want to create a subtype for a specific, partial list of keys from the object, which you want to treat differently. Below you see an example where this `Extends` type function is used to make sure that you can only create the subtype with types from the union.

```ts
type Extends<T, U extends T> = U;

type Special = string
type DataTransferObject = {
  normalKey1: string;
  normalKey2: number;
  specialKey1: Special;
  specialKey2: Special;
};
type ValidSubtype = Extends<
  keyof DataTransferObject,
  "specialKey1" | "specialKey2"
>;

// Error
type InvalidSubtype = Extends<
  keyof DataTransferObject,
  "specialKey1" | "specialKey2" | "zcvz"
>;

const validUsage: Set<ValidSubtype> = new Set(["specialKey1", "specialKey2"]);

// Error
const invalidUsage: Set<ValidSubtype> = new Set(["specialKey1", "asdasd"]);
```

_Play with this example on the [typescript playground](https://www.typescriptlang.org/play?#code/KYDwDg9gTgLgBDAnmYcCiIbAHYBMDOAPACoA0cAqnKFnvnMQHxwC8lA3AFCdIpwDKKAMYBLAIYAbVnHwwoI7AHMeyVABExMMcShjs+AGbAoAeQBGAK2BD4bAN6c4cbNAC2kgNLBEARgBcMnIKilxOLlDuEl6IAEwB2ACurmbGoTLC4lHe-gIZkmn4eVmxAYLWmVwAvly8qABqkiK4-AlmtdIYtASEjnAA1t4QBnAaWjp6hsbmVjakvQBEheWe2fNwAD5wi0XRMfOcjFycAPTH6FBQ0Cp8AJLYAG6Nza3tbJ043b0DiEMjmtq6fRGUyWawwOZObbLYo+NabKGiFaxOFbABeQnuqP2h24Qgg+ngjwkTQo+DEimApWAMEIDWJzzaqmYbGwwAA7gJqQAKADaCMy0Vh5H5SL2AF0AJRHU7nS5QTh4glwBREklkilUml0potRkoZnOdmcmC8kUw+bCsT4XBW3DzSVcIA)_

Source: [Stack overflow](https://stackoverflow.com/a/53637746/2696423)