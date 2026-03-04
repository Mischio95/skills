---
name: typescript-advanced-types
description: Master TypeScript's advanced type system including generics, conditional types, mapped types, template literals, utility types, and modern features like `satisfies` and `const type parameters`. Use when implementing complex type logic, creating reusable type utilities, ensuring compile-time type safety, or building type-safe APIs, libraries, and frameworks in TypeScript projects.
---

# TypeScript Advanced Types

Comprehensive guidance for mastering TypeScript's advanced type system — generics, conditional types, mapped types, template literal types, utility types, and modern TypeScript 5.x features — for building robust, type-safe applications.

## When to Use This Skill

- Building type-safe libraries or frameworks
- Creating reusable generic components
- Implementing complex type inference logic
- Designing type-safe API clients or SDKs
- Building form validation systems with type-safe schemas
- Creating strongly-typed configuration objects
- Implementing type-safe state management (Redux, Zustand, XState)
- Migrating JavaScript codebases to TypeScript
- Wrapping third-party libraries with better types
- Writing type-level tests to validate type behavior

## Core Concepts

### 1. Generics

**Purpose:** Create reusable, type-flexible components while maintaining type safety.

**Basic Generic Function:**

```typescript
function identity<T>(value: T): T {
  return value;
}

const num = identity<number>(42); // Type: number
const str = identity<string>("hello"); // Type: string
const auto = identity(true); // Type inferred: boolean
```

**Generic Constraints:**

```typescript
interface HasLength {
  length: number;
}

function logLength<T extends HasLength>(item: T): T {
  console.log(item.length);
  return item;
}

logLength("hello"); // OK: string has length
logLength([1, 2, 3]); // OK: array has length
logLength({ length: 10 }); // OK: object has length
// logLength(42);             // Error: number has no length
```

**Multiple Type Parameters:**

```typescript
function merge<T, U>(obj1: T, obj2: U): T & U {
  return { ...obj1, ...obj2 };
}

const merged = merge({ name: "John" }, { age: 30 });
// Type: { name: string } & { age: number }
```

**Default Type Parameters:**

```typescript
interface APIResponse<TData = unknown, TError = string> {
  data?: TData;
  error?: TError;
  status: number;
}

// Uses defaults
const res1: APIResponse = { status: 200 };
// Custom types
const res2: APIResponse<User, AppError> = { data: user, status: 200 };
```

**Const Type Parameters (TypeScript 5.0+):**

```typescript
// Without const: T is inferred as string[]
function routes<T extends readonly string[]>(paths: T): T {
  return paths;
}
const r1 = routes(["home", "about"]); // Type: string[]

// With const: T preserves literal types
function routesConst<const T extends readonly string[]>(paths: T): T {
  return paths;
}
const r2 = routesConst(["home", "about"]); // Type: readonly ["home", "about"]

// Useful for creating type-safe mappings
function createEnum<const T extends Record<string, string>>(obj: T): T {
  return Object.freeze(obj);
}

const Status = createEnum({
  Active: "ACTIVE",
  Inactive: "INACTIVE",
  Pending: "PENDING",
});
// Type: { readonly Active: "ACTIVE"; readonly Inactive: "INACTIVE"; readonly Pending: "PENDING" }
```

### 2. Conditional Types

**Purpose:** Create types that depend on conditions, enabling sophisticated type logic.

**Basic Conditional Type:**

```typescript
type IsString<T> = T extends string ? true : false;

type A = IsString<string>; // true
type B = IsString<number>; // false
```

**Extracting Return Types:**

```typescript
// Note: ReturnType<T> is already built-in in TypeScript.
// This is shown for educational purposes to understand how it works internally.
type MyReturnType<T> = T extends (...args: any[]) => infer R ? R : never;

function getUser() {
  return { id: 1, name: "John" };
}

type User = ReturnType<typeof getUser>;
// Type: { id: number; name: string; }
```

**Distributive Conditional Types:**

```typescript
type ToArray<T> = T extends any ? T[] : never;

type StrOrNumArray = ToArray<string | number>;
// Type: string[] | number[] (distributes over the union)

// Prevent distribution with tuple wrapping:
type ToArrayNonDist<T> = [T] extends [any] ? T[] : never;

type StrOrNumArrayNonDist = ToArrayNonDist<string | number>;
// Type: (string | number)[] (does NOT distribute)
```

**Nested Conditions:**

```typescript
type TypeName<T> = T extends string
  ? "string"
  : T extends number
    ? "number"
    : T extends boolean
      ? "boolean"
      : T extends undefined
        ? "undefined"
        : T extends Function
          ? "function"
          : "object";

type T1 = TypeName<string>; // "string"
type T2 = TypeName<() => void>; // "function"
```

### 3. Mapped Types

**Purpose:** Transform existing types by iterating over their properties.

**Basic Mapped Type:**

```typescript
// Note: Readonly<T> is already built-in in TypeScript.
// This demonstrates how mapped types work internally.
type MyReadonly<T> = {
  readonly [P in keyof T]: T[P];
};

interface User {
  id: number;
  name: string;
}

type ReadonlyUser = Readonly<User>;
// Type: { readonly id: number; readonly name: string; }
```

**Optional Properties:**

```typescript
// Note: Partial<T> is already built-in in TypeScript.
type MyPartial<T> = {
  [P in keyof T]?: T[P];
};

type PartialUser = Partial<User>;
// Type: { id?: number; name?: string; }
```

**Key Remapping (TypeScript 4.1+):**

```typescript
type Getters<T> = {
  [K in keyof T as `get${Capitalize<string & K>}`]: () => T[K];
};

interface Person {
  name: string;
  age: number;
}

type PersonGetters = Getters<Person>;
// Type: { getName: () => string; getAge: () => number; }
```

**Filtering Properties:**

```typescript
type PickByType<T, U> = {
  [K in keyof T as T[K] extends U ? K : never]: T[K];
};

interface Mixed {
  id: number;
  name: string;
  age: number;
  active: boolean;
}

type OnlyNumbers = PickByType<Mixed, number>;
// Type: { id: number; age: number; }
```

### 4. Template Literal Types

**Purpose:** Create string-based types with pattern matching and transformation.

**Basic Template Literal:**

```typescript
type EventName = "click" | "focus" | "blur";
type EventHandler = `on${Capitalize<EventName>}`;
// Type: "onClick" | "onFocus" | "onBlur"
```

**String Manipulation Types:**

```typescript
type UppercaseGreeting = Uppercase<"hello">; // "HELLO"
type LowercaseGreeting = Lowercase<"HELLO">; // "hello"
type CapitalizedName = Capitalize<"john">; // "John"
type UncapitalizedName = Uncapitalize<"John">; // "john"
```

**Recursive Path Building:**

```typescript
type Path<T> = T extends object
  ? {
      [K in keyof T]: K extends string
        ? `${K}` | `${K}.${Path<T[K]>}`
        : never;
    }[keyof T]
  : never;

interface Config {
  server: {
    host: string;
    port: number;
  };
  database: {
    url: string;
  };
}

type ConfigPath = Path<Config>;
// Type: "server" | "database" | "server.host" | "server.port" | "database.url"
```

**Parsing Template Literals:**

```typescript
// Extract route parameters from URL patterns
type ExtractParams<T extends string> =
  T extends `${string}:${infer Param}/${infer Rest}`
    ? Param | ExtractParams<Rest>
    : T extends `${string}:${infer Param}`
      ? Param
      : never;

type Params = ExtractParams<"/users/:userId/posts/:postId">;
// Type: "userId" | "postId"
```

### 5. Utility Types

**Built-in Utility Types:**

```typescript
// Partial<T> - Make all properties optional
type PartialUser = Partial<User>;

// Required<T> - Make all properties required
type RequiredUser = Required<PartialUser>;

// Readonly<T> - Make all properties readonly
type ReadonlyUser = Readonly<User>;

// Pick<T, K> - Select specific properties
type UserName = Pick<User, "name" | "email">;

// Omit<T, K> - Remove specific properties
type UserWithoutPassword = Omit<User, "password">;

// Exclude<T, U> - Exclude types from union
type T1 = Exclude<"a" | "b" | "c", "a">; // "b" | "c"

// Extract<T, U> - Extract types from union
type T2 = Extract<"a" | "b" | "c", "a" | "b">; // "a" | "b"

// NonNullable<T> - Exclude null and undefined
type T3 = NonNullable<string | null | undefined>; // string

// Record<K, T> - Create object type with keys K and values T
type PageInfo = Record<"home" | "about", { title: string }>;

// Awaited<T> (TypeScript 4.5+) - Recursively unwrap Promise types
type ResolvedValue = Awaited<Promise<Promise<string>>>; // string

// NoInfer<T> (TypeScript 5.4+) - Prevent inference from a specific position
function createFSM<TState extends string>(config: {
  initial: NoInfer<TState>;
  states: TState[];
}) {
  return config;
}
// Without NoInfer, `initial` could widen the TState union.
// With NoInfer, `initial` must be one of the values in `states`.
createFSM({ initial: "idle", states: ["idle", "running", "stopped"] }); // OK
// createFSM({ initial: "unknown", states: ["idle", "running"] }); // Error!
```

### 6. The `satisfies` Operator (TypeScript 4.9+)

**Purpose:** Validate that an expression matches a type without widening the inferred type.

```typescript
type Color = "red" | "green" | "blue";
type ColorMap = Record<Color, string | [number, number, number]>;

// With type annotation: loses specific info
const colorsAnnotated: ColorMap = {
  red: [255, 0, 0],
  green: "#00ff00",
  blue: [0, 0, 255],
};
colorsAnnotated.green.toUpperCase(); // Error: string | [number, number, number] has no toUpperCase

// With satisfies: validates AND preserves narrow types
const colors = {
  red: [255, 0, 0],
  green: "#00ff00",
  blue: [0, 0, 255],
} satisfies ColorMap;

colors.green.toUpperCase(); // OK! TypeScript knows green is string
colors.red[0]; // OK! TypeScript knows red is [number, number, number]

// Combined with as const for maximum precision
const routes = {
  home: "/",
  about: "/about",
  user: "/user/:id",
} as const satisfies Record<string, `/${string}`>;

// routes.home is typed as "/" (not string)
```

## Advanced Patterns

### Pattern 1: Type-Safe Event Emitter

```typescript
type EventMap = {
  "user:created": { id: string; name: string };
  "user:updated": { id: string; changes: Record<string, unknown> };
  "user:deleted": { id: string };
};

class TypedEventEmitter<T extends Record<string, any>> {
  private listeners: {
    [K in keyof T]?: Array<(data: T[K]) => void>;
  } = {};

  on<K extends keyof T>(event: K, callback: (data: T[K]) => void): () => void {
    if (!this.listeners[event]) {
      this.listeners[event] = [];
    }
    this.listeners[event]!.push(callback);
    // Return unsubscribe function
    return () => {
      this.listeners[event] = this.listeners[event]?.filter((cb) => cb !== callback);
    };
  }

  emit<K extends keyof T>(event: K, data: T[K]): void {
    const callbacks = this.listeners[event];
    if (callbacks) {
      callbacks.forEach((callback) => callback(data));
    }
  }

  off<K extends keyof T>(event: K): void {
    delete this.listeners[event];
  }
}

const emitter = new TypedEventEmitter<EventMap>();

const unsubscribe = emitter.on("user:created", (data) => {
  console.log(data.id, data.name); // Fully type-safe!
});

emitter.emit("user:created", { id: "1", name: "John" });
// emitter.emit("user:created", { id: "1" });  // Error: missing 'name'
unsubscribe(); // Clean up
```

### Pattern 2: Type-Safe API Client

```typescript
type HTTPMethod = "GET" | "POST" | "PUT" | "DELETE";

interface User {
  id: string;
  name: string;
  email: string;
}

type EndpointConfig = {
  "/users": {
    GET: { response: User[] };
    POST: { body: { name: string; email: string }; response: User };
  };
  "/users/:id": {
    GET: { params: { id: string }; response: User };
    PUT: { params: { id: string }; body: Partial<User>; response: User };
    DELETE: { params: { id: string }; response: void };
  };
};

type ExtractParams<T> = T extends { params: infer P } ? P : never;
type ExtractBody<T> = T extends { body: infer B } ? B : never;
type ExtractResponse<T> = T extends { response: infer R } ? R : never;

class APIClient<Config extends Record<string, Partial<Record<HTTPMethod, any>>>> {
  async request<
    Path extends keyof Config & string,
    Method extends keyof Config[Path] & string,
  >(
    path: Path,
    method: Method,
    ...[options]: ExtractParams<Config[Path][Method]> extends never
      ? ExtractBody<Config[Path][Method]> extends never
        ? []
        : [{ body: ExtractBody<Config[Path][Method]> }]
      : [
          {
            params: ExtractParams<Config[Path][Method]>;
            body?: ExtractBody<Config[Path][Method]>;
          },
        ]
  ): Promise<ExtractResponse<Config[Path][Method]>> {
    // Implementation: build URL, replace params, fetch, etc.
    return {} as any;
  }
}

const api = new APIClient<EndpointConfig>();

// Type-safe API calls
const users = await api.request("/users", "GET");
// Type: User[]

const newUser = await api.request("/users", "POST", {
  body: { name: "John", email: "john@example.com" },
});
// Type: User

const user = await api.request("/users/:id", "GET", {
  params: { id: "123" },
});
// Type: User
```

### Pattern 3: Builder Pattern with Type Safety

```typescript
type RequiredKeys<T> = {
  [K in keyof T]-?: {} extends Pick<T, K> ? never : K;
}[keyof T];

// Track which required keys have been set
type HasAllRequired<T, Set extends keyof T> = RequiredKeys<T> extends Set
  ? true
  : false;

class Builder<T extends Record<string, any>, Set extends keyof T = never> {
  private state: Partial<T> = {};

  set<K extends keyof T>(
    key: K,
    value: T[K],
  ): Builder<T, Set | K> {
    (this.state as any)[key] = value;
    return this as any;
  }

  // build() is only callable when all required keys have been set
  build(
    this: HasAllRequired<T, Set> extends true ? Builder<T, Set> : never,
  ): T {
    return this.state as T;
  }
}

interface UserConfig {
  id: string;
  name: string;
  email: string;
  age?: number;
  bio?: string;
}

const user = new Builder<UserConfig>()
  .set("id", "1")
  .set("name", "John")
  .set("email", "john@example.com")
  .set("age", 30) // optional, but type-safe
  .build(); // OK: all required fields set

// const incomplete = new Builder<UserConfig>()
//   .set("id", "1")
//   .build(); // Error: 'name' and 'email' are missing
```

### Pattern 4: Deep Readonly / Deep Partial

```typescript
type DeepReadonly<T> = T extends Function
  ? T
  : T extends Map<infer K, infer V>
    ? ReadonlyMap<DeepReadonly<K>, DeepReadonly<V>>
    : T extends Set<infer U>
      ? ReadonlySet<DeepReadonly<U>>
      : T extends object
        ? { readonly [P in keyof T]: DeepReadonly<T[P]> }
        : T;

type DeepPartial<T> = T extends Function
  ? T
  : T extends Array<infer U>
    ? Array<DeepPartial<U>>
    : T extends object
      ? { [P in keyof T]?: DeepPartial<T[P]> }
      : T;

interface AppConfig {
  server: {
    host: string;
    port: number;
    ssl: {
      enabled: boolean;
      cert: string;
    };
  };
  database: {
    url: string;
    pool: {
      min: number;
      max: number;
    };
  };
}

type ReadonlyConfig = DeepReadonly<AppConfig>;
// All nested properties are readonly — prevents accidental mutation

type PartialConfig = DeepPartial<AppConfig>;
// All nested properties are optional — useful for config overrides
```

### Pattern 5: Type-Safe Form Validation

```typescript
type ValidationRule<T> = {
  validate: (value: T) => boolean;
  message: string;
};

type FieldValidation<T> = {
  [K in keyof T]?: ValidationRule<T[K]>[];
};

type ValidationErrors<T> = {
  [K in keyof T]?: string[];
};

class FormValidator<T extends Record<string, any>> {
  constructor(private rules: FieldValidation<T>) {}

  validate(data: T): ValidationErrors<T> | null {
    const errors: ValidationErrors<T> = {};
    let hasErrors = false;

    for (const key in this.rules) {
      const fieldRules = this.rules[key];
      const value = data[key];

      if (fieldRules) {
        const fieldErrors: string[] = [];

        for (const rule of fieldRules) {
          if (!rule.validate(value)) {
            fieldErrors.push(rule.message);
          }
        }

        if (fieldErrors.length > 0) {
          errors[key] = fieldErrors;
          hasErrors = true;
        }
      }
    }

    return hasErrors ? errors : null;
  }
}

interface LoginForm {
  email: string;
  password: string;
}

const validator = new FormValidator<LoginForm>({
  email: [
    {
      validate: (v) => v.length > 0,
      message: "Email is required",
    },
    {
      validate: (v) => v.includes("@"),
      message: "Email must contain @",
    },
  ],
  password: [
    {
      validate: (v) => v.length >= 8,
      message: "Password must be at least 8 characters",
    },
  ],
});

const errors = validator.validate({
  email: "invalid",
  password: "short",
});
// Type: { email?: string[]; password?: string[]; } | null
```

### Pattern 6: Discriminated Unions and State Machines

```typescript
// Use distinct names to avoid shadowing the global Error type
type SuccessState<T> = {
  status: "success";
  data: T;
};

type ErrorState = {
  status: "error";
  error: string;
};

type LoadingState = {
  status: "loading";
};

type AsyncState<T> = SuccessState<T> | ErrorState | LoadingState;

function handleState<T>(state: AsyncState<T>): void {
  switch (state.status) {
    case "success":
      console.log(state.data); // Type: T — narrowed automatically
      break;
    case "error":
      console.log(state.error); // Type: string — narrowed automatically
      break;
    case "loading":
      console.log("Loading...");
      break;
  }
}

// Exhaustive check helper — causes a compile error if a case is missed
function assertNever(value: never): never {
  throw new Error(`Unexpected value: ${value}`);
}

// Type-safe state machine with exhaustive transitions
type MachineState =
  | { type: "idle" }
  | { type: "fetching"; requestId: string }
  | { type: "success"; data: unknown }
  | { type: "error"; message: string };

type MachineEvent =
  | { type: "FETCH"; requestId: string }
  | { type: "SUCCESS"; data: unknown }
  | { type: "ERROR"; message: string }
  | { type: "RESET" };

function reducer(state: MachineState, event: MachineEvent): MachineState {
  switch (state.type) {
    case "idle":
      return event.type === "FETCH"
        ? { type: "fetching", requestId: event.requestId }
        : state;
    case "fetching":
      if (event.type === "SUCCESS") return { type: "success", data: event.data };
      if (event.type === "ERROR") return { type: "error", message: event.message };
      return state;
    case "success":
    case "error":
      return event.type === "RESET" ? { type: "idle" } : state;
    default:
      return assertNever(state);
  }
}
```

### Pattern 7: Variadic Tuple Types (TypeScript 4.0+)

```typescript
// Concatenate two tuple types
type Concat<A extends unknown[], B extends unknown[]> = [...A, ...B];

type AB = Concat<[string, number], [boolean]>;
// Type: [string, number, boolean]

// Type-safe curry function
type Head<T extends any[]> = T extends [infer H, ...any[]] ? H : never;
type Tail<T extends any[]> = T extends [any, ...infer R] ? R : never;

// Typed pipeline
function pipe<A, B>(fn1: (a: A) => B): (a: A) => B;
function pipe<A, B, C>(fn1: (a: A) => B, fn2: (b: B) => C): (a: A) => C;
function pipe<A, B, C, D>(fn1: (a: A) => B, fn2: (b: B) => C, fn3: (c: C) => D): (a: A) => D;
function pipe(...fns: Function[]) {
  return (arg: any) => fns.reduce((prev, fn) => fn(prev), arg);
}

const transform = pipe(
  (x: string) => x.length,    // string → number
  (x: number) => x > 5,       // number → boolean
);
// Type: (a: string) => boolean
```

## Type Inference Techniques

### 1. The `infer` Keyword

```typescript
// Extract array element type
type ElementType<T> = T extends (infer U)[] ? U : never;

type NumArray = number[];
type Num = ElementType<NumArray>; // number

// Extract promise type (recursively)
type PromiseType<T> = T extends Promise<infer U> ? PromiseType<U> : T;

type AsyncNum = PromiseType<Promise<Promise<number>>>; // number

// Extract function parameters
// Note: Parameters<T> is already built-in. Shown for educational purposes.
type MyParameters<T> = T extends (...args: infer P) => any ? P : never;

function foo(a: string, b: number) {}
type FooParams = Parameters<typeof foo>; // [string, number]
```

### 2. Infer in Multiple Positions

```typescript
// Extract first and last elements of a tuple
type FirstAndLast<T extends any[]> = T extends [infer F, ...any[], infer L]
  ? [F, L]
  : never;

type FL = FirstAndLast<[1, 2, 3, 4]>; // [1, 4]

// Infer in covariant position: union of candidates
type CovariantInfer<T> = T extends { a: infer U; b: infer U } ? U : never;
type Covariant = CovariantInfer<{ a: string; b: number }>; // string | number

// Infer in contravariant position: intersection of candidates
type ContravariantInfer<T> = T extends {
  a: (x: infer U) => void;
  b: (x: infer U) => void;
} ? U : never;
type Contravariant = ContravariantInfer<{
  a: (x: string) => void;
  b: (x: number) => void;
}>; // string & number (i.e., never)

// Practical use: extract union from overloaded function
type OverloadReturnTypes<T> = T extends {
  (...args: any[]): infer R1;
  (...args: any[]): infer R2;
} ? R1 | R2 : never;
```

### 3. Type Guards

```typescript
function isString(value: unknown): value is string {
  return typeof value === "string";
}

function isNumber(value: unknown): value is number {
  return typeof value === "number";
}

function isArrayOf<T>(
  value: unknown,
  guard: (item: unknown) => item is T,
): value is T[] {
  return Array.isArray(value) && value.every(guard);
}

const data: unknown = ["a", "b", "c"];

if (isArrayOf(data, isString)) {
  data.forEach((s) => s.toUpperCase()); // Type: string[]
}

// Discriminated union type guard
function isErrorState(state: AsyncState<unknown>): state is ErrorState {
  return state.status === "error";
}
```

### 4. Assertion Functions

```typescript
function assertIsString(value: unknown): asserts value is string {
  if (typeof value !== "string") {
    throw new Error(`Expected string, got ${typeof value}`);
  }
}

function assertDefined<T>(value: T | null | undefined): asserts value is T {
  if (value === null || value === undefined) {
    throw new Error("Value is null or undefined");
  }
}

function processValue(value: unknown) {
  assertIsString(value);
  // value is now typed as string — no cast needed
  console.log(value.toUpperCase());
}
```

## Best Practices

1. **Use `unknown` over `any`** — Enforce type checking at the call site; `any` defeats TypeScript's purpose
2. **Prefer `interface` for object shapes** — Better error messages and supports declaration merging
3. **Use `type` for unions, intersections, and complex types** — More flexible composition
4. **Leverage type inference** — Let TypeScript infer when possible; annotate only when inference is insufficient
5. **Use `satisfies` for validation without widening** — Get both type checking and narrow inference
6. **Use `const` type parameters** — Preserve literal types in generic functions (TS 5.0+)
7. **Create helper types** — Build reusable type utilities for common patterns
8. **Use const assertions (`as const`)** — Preserve literal types and make objects deeply readonly
9. **Avoid type assertions (`as`)** — Use type guards and assertion functions instead
10. **Document complex types** — Add JSDoc comments explaining the purpose and constraints
11. **Use strict mode** — Enable all strict compiler options (`strict: true` in tsconfig)
12. **Test your types** — Use type-level tests to verify behavior (see Type Testing below)
13. **Prefer discriminated unions** — Enables exhaustive type narrowing in switch/if blocks
14. **Use `NoInfer<T>`** — Prevent unwanted type widening in generic functions (TS 5.4+)

## Type Testing

```typescript
// Strict type equality test
type Expect<T extends true> = T;
type Equal<X, Y> =
  (<T>() => T extends X ? 1 : 2) extends (<T>() => T extends Y ? 1 : 2)
    ? true
    : false;

// Usage: compile-time type tests (errors if the type is wrong)
type _Test1 = Expect<Equal<string, string>>; // OK
type _Test2 = Expect<Equal<number, number>>; // OK
// type _Test3 = Expect<Equal<string, number>>; // Error! Types are not equal

// Test with utility types
type _TestPartial = Expect<
  Equal<Partial<{ a: string; b: number }>, { a?: string; b?: number }>
>;

// Test conditional types
type _TestIsString1 = Expect<Equal<IsString<string>, true>>;
type _TestIsString2 = Expect<Equal<IsString<number>, false>>;

// Expect a type to be assignable to another
type IsAssignableTo<T, U> = T extends U ? true : false;
type _TestAssignable = Expect<IsAssignableTo<"hello", string>>; // OK
```

## Common Pitfalls

1. **Over-using `any`** — Defeats the purpose of TypeScript; use `unknown` and narrow
2. **Ignoring strict null checks** — Can lead to `undefined is not an object` at runtime
3. **Over-engineering types** — Complex types slow down IDE performance and confuse consumers
4. **Shadowing built-in types** — Avoid naming custom types `Error`, `Object`, `Function`, etc.
5. **Not using discriminated unions** — Misses type narrowing opportunities; use a `type` or `status` discriminant
6. **Forgetting `readonly`** — Allows unintended mutations; use `Readonly<T>`, `as const`, or `DeepReadonly<T>`
7. **Circular type references** — Can cause infinite recursion; add a recursion bound or depth limit
8. **Not handling edge cases** — Empty arrays, `null`, `undefined`, empty strings — guard for all of them
9. **Ignoring distributive behavior** — Conditional types distribute over unions by default; wrap in `[T]` to prevent
10. **Using `as` to silence errors** — Masks bugs; prefer refactoring the types to be correct

## Performance Considerations

- **Limit conditional type depth** — TypeScript has a recursion limit of ~50 levels; keep recursive types under 20 levels for good IDE performance
- **Use tail-recursive types (TS 4.5+)** — Accumulator-pattern recursive types get optimized by the compiler
- **Avoid excessive mapped type combinations** — Each mapped type creates a new type; chaining many mapped types can slow compilation
- **Simplify union types** — Unions over ~25 members start impacting performance; consider grouping with branded types
- **Cache complex computations** — Extract intermediate types into named aliases so they're computed once
- **Use `interface extends` over intersection `&`** — Interfaces are cached by name; intersections are recomputed
- **Profile with `--generateTrace`** — Run `tsc --generateTrace traceDir` to identify slow types in your project
- **Skip type checking in CI builds** — Use `tsc --noEmit` for type checking separately, `esbuild`/`swc` for bundling

## Resources

- **TypeScript Handbook**: https://www.typescriptlang.org/docs/handbook/
- **Type Challenges**: https://github.com/type-challenges/type-challenges
- **TypeScript Deep Dive**: https://basarat.gitbook.io/typescript/
- **Effective TypeScript** (2nd ed.): Book by Dan Vanderkam
- **Total TypeScript**: https://www.totaltypescript.com/
- **TypeScript Release Notes**: https://devblogs.microsoft.com/typescript/
