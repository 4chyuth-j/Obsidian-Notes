# 🚀What is typescript?

**TypeScript** is a **superset of JavaScript** that adds **static typing** to the language.

### 🌟 In Simple Terms:

> TypeScript = JavaScript + Type Safety

---

### 🧠 Why Use TypeScript?

JavaScript is dynamic, which means it doesn't check for errors like:

```js
let x = "hello";
x = 123;  // This is valid in JS, but might cause bugs!
```

TypeScript catches these mistakes **before** the code runs:

```ts
let x: string = "hello";
x = 123; // ❌ Error: Type 'number' is not assignable to type 'string'
```

---

### 🔑 Key Features of TypeScript:

- ✅ **Type annotations**: Declare variable types (`string`, `number`, `boolean`, etc.)
    
- 🏗️ **Interfaces** and **Types**: Define the structure of objects and functions
    
- 🧱 **Classes and OOP**: Supports object-oriented programming (inheritance, encapsulation, etc.)
    
- 🛡️ **Compile-time checks**: Errors caught while coding instead of during runtime
    
- 🚀 **Tooling support**: Works well with modern editors like VS Code (auto-complete, hints)
    

---

### 🧪 Example:

```ts
function greet(name: string): string {
  return "Hello, " + name;
}

greet("Achyuth");     // ✅ OK
greet(123);           // ❌ Error: Argument of type 'number' is not assignable to parameter of type 'string'
```

---

### 🔄 TypeScript vs JavaScript

|Feature|JavaScript|TypeScript|
|---|---|---|
|Type Safety|❌ No|✅ Yes|
|Compile-time Errors|❌ No|✅ Yes|
|OOP Support|😐 Basic|✅ Full Support|
|Learning Curve|✅ Easy|⚠️ Slightly higher|
|Runs in Browser|✅ Yes|🚫 Needs compilation|

---

### ⚙️ How It Works

1. You write `.ts` files (TypeScript)
    
2. TypeScript compiles it into `.js` (plain JavaScript)
    
3. That JavaScript runs in any browser or Node.js
    

---

### 🛠️ Real-World Usage

- Used by big companies like **Microsoft, Google, Slack, Airbnb**
    
- Popular in **Angular**, **Next.js**, and **React** projects
    
- Great for **large-scale applications** with many developers
    

---



# 🚀What is Type in typescript?

In **TypeScript**, a **type** describes what kind of data a variable, parameter, or function can hold or return.

Think of a type as a **label** that says:

> “This thing is a number” or “This thing is a string” or “This thing can be one of these two shapes.”

Types help TypeScript **catch mistakes before your code runs**.

---

## 🔹 Why Types Matter

In plain JavaScript:

```js
let age = 25;
age = "twenty-five"; // No error, but might break something later
```

In TypeScript:

```ts
let age: number = 25;
age = "twenty-five"; // ❌ Error: Type 'string' is not assignable to type 'number'
```

---

## 🔑 Common Types in TypeScript

### 1. **Primitive Types**

- `string` → text
    
- `number` → numbers (both int & float)
    
- `boolean` → true/false
    
- `null`, `undefined`, `symbol`, `bigint`
    

Example:

```ts
let name: string = "Achyuth";
let age: number = 25;
let isStudent: boolean = true;
```

---

### 2. **Array Type**

```ts
let numbers: number[] = [1, 2, 3];
let fruits: string[] = ["apple", "banana"];
```

---

### 3. **Tuple Type**

Fixed length & specific types:

```ts
let person: [string, number] = ["Achyuth", 25];
```

---

### 4. **Union Types**

Allow multiple types:

```ts
let id: number | string;
id = 101;
id = "abc"; // Both OK
```

---

### 5. **Literal Types**

Restrict to specific values:

```ts
let direction: "up" | "down";
direction = "up"; // ✅
direction = "left"; // ❌
```

---

### 6. **Object Type**

Shape of an object:

```ts
let user: { name: string; age: number } = { name: "Achyuth", age: 25 };
```

---

### 7. **Function Types**

Specifying parameter and return types:

```ts
function greet(name: string): string {
  return "Hello " + name;
}
```

---

### 8. **Any & Unknown**

- `any` → disables type checking (use rarely)
    
- `unknown` → must check type before using
    

---

### 9. **Custom Types**

You can create your own using **type aliases** or **interfaces**:

```ts
type User = { name: string; age: number };

interface Product {
  id: number;
  title: string;
}
```

---

💡 **In short:**

> Types in TypeScript define the _kind_ of data and its _structure_, so you can write safer, more predictable code.

---


# 🚀What is type inference?

Type inference in **TypeScript** is when the compiler automatically figures out the type of a variable, parameter, or return value **without you explicitly specifying it**.

In simple words — TypeScript looks at the value you’ve assigned and guesses the type for you.

---

### Example

```typescript
let num = 10;  
// TypeScript infers this as: let num: number

let name = "Achyuth";
// Inferred as: let name: string

function add(a: number, b: number) {
  return a + b;
}
// Return type is automatically inferred as number
```

---

### How it works

TypeScript uses:

1. **Initial value** → If you assign something during declaration, TypeScript uses it to infer the type.
    
2. **Function return** → It looks at your return statement and decides the return type.
    
3. **Contextual typing** → It infers type from where the value is used.
    

Example of contextual typing:

```typescript
window.onmousedown = function (event) {
  console.log(event.button); // event is inferred as MouseEvent
};
```

---

### Why it’s useful

- Saves time (you don’t have to write types everywhere).
    
- Keeps code clean but still type-safe.
    
- Reduces repetition.
    

---

💡 **Tip:** If TypeScript can’t figure out the type, it assigns `any` — which means you lose type safety. That’s when you should manually specify the type.

---

# 🚀What is type `any`?

TypeScript also has a special type, `any`, that you can use whenever you don’t want a particular value to cause typechecking errors.

When a value is of type `any`, you can access any properties of it (which will in turn be of type `any`), call it like a function, assign it to (or from) a value of any type, or pretty much anything else that’s syntactically legal:

```typescript
let obj: any = { x: 0 };  
   // None of the following lines of code will throw compiler errors.  
   // Using `any` disables all further type checking, and it is assumed 
    // you know the environment better than TypeScript.  
obj.foo();  
obj();  obj.bar = 100;  
obj = "hello";  
const n: number = obj;   
```


The `any` type is useful when you don’t want to write out a long type just to convince TypeScript that a particular line of code is okay.

### `noImplicitAny`

When you don’t specify a type, and TypeScript can’t infer it from context, the compiler will typically default to `any`.

You usually want to avoid this, though, because `any` isn’t type-checked. Use the compiler flag [`noImplicitAny`](https://www.typescriptlang.org/tsconfig#noImplicitAny) to flag any implicit `any` as an error.


# 🚀Functions typing
In TypeScript, **functions are typed** by specifying types for:

1. **Parameters**
    
2. **Return type**
    
3. (Optionally) `this` context and type parameters (for generics)
    

The idea is:

```
(parameter1: Type1, parameter2: Type2, ...) => ReturnType
```

---

## **1. Typing Parameters**

You explicitly declare the type for each parameter.

```ts
function add(a: number, b: number) {
  return a + b;
}
```

- Here, `a` and `b` must be numbers.
    
- If you pass anything else, TypeScript will throw a compile-time error.
    

---

## **2. Typing Return Value**

You can explicitly set the return type after the parameter list with a colon `:`.

```ts
function greet(name: string): string {
  return `Hello, ${name}`;
}
```

- Explicit return type helps catch accidental returns of the wrong type.
    

---

## **3. Optional Parameters**

Marked with `?`, meaning they can be omitted (value will be `undefined` if not passed).

```ts
function greet(name: string, age?: number): string {
  return age ? `${name} is ${age}` : `${name} has no age`;
}
```

---

## **4. Default Parameters**

Set a default value so TypeScript infers the type automatically.

```ts
function greet(name: string = "Guest"): string {
  return `Hello, ${name}`;
}
```

---

## **5. Function Type Signatures**

You can define a variable that stores a function, using a **function type**.

```ts
let greet: (name: string) => string;

greet = (name) => `Hello, ${name}`;
```

---

## **6. Using Type Aliases for Function Types**

Makes the function signature reusable.

```ts
type GreetFn = (name: string) => string;

const greet: GreetFn = (name) => `Hello, ${name}`;
```

---

## **7. Using Interfaces for Function Types**

Interfaces can also define callable types.

```ts
interface GreetFn {
  (name: string): string;
}

const greet: GreetFn = (name) => `Hello, ${name}`;
```

---

## **8. Function Overloading**

Multiple type signatures for one implementation.

```ts
function combine(a: number, b: number): number;
function combine(a: string, b: string): string;
function combine(a: any, b: any) {
  return a + b;
}
```

---

## **9. Typing `this` in Functions**

TypeScript allows you to explicitly type `this` for methods.

```ts
function sayHello(this: { name: string }) {
  console.log(`Hello, ${this.name}`);
}
```

---

## **10. Generics in Functions**

Type-safe functions that work with any type.

```ts
function identity<T>(value: T): T {
  return value;
}

console.log(identity<string>("Achyuth"));
console.log(identity<number>(42));
```

---

If you want, I can make you a **single cheat sheet** that shows **all ways to type functions in TypeScript** side-by-side so you can compare them at a glance.  
That’ll make revision super easy.


# 🚀Bad object behavior(focus point 3)


## **1. Objects are passed by reference**

When you pass an object to a function, you’re passing the **reference** (pointer) to the same memory location — not a copy.

```ts
function changeUser(user: { name: string }) {
  user.name = "Changed";
}

let person = { name: "Achyuth" };
changeUser(person);

console.log(person.name); // ⚠ "Changed"
```

- Even though it’s inside the function, the original object gets modified.
    
- TypeScript **won’t warn you** — it assumes this is intentional.
    

---

## **2. Unintentional mutations**

If you meant to keep the original object safe, you have to **clone** it yourself:

```ts
function changeUser(user: { name: string }) {
  let copy = { ...user };
  copy.name = "Changed";
  return copy;
}

let person = { name: "Achyuth" };
let newPerson = changeUser(person);

console.log(person.name); // ✅ "Achyuth"
```

---

## **3. Extra property checks**

TypeScript is stricter when you pass **inline objects**:

```ts
function printUser(user: { name: string }) {}
printUser({ name: "Achyuth", age: 25 }); // ❌ Error: 'age' is not allowed
```

But if you store it in a variable first:

```ts
let person = { name: "Achyuth", age: 25 };
printUser(person); // ✅ Works (excess property check skipped)
```

⚠ This can lead to “hidden” properties being passed around unexpectedly.

---

## **4. Readonly doesn’t stop nested mutations**

```ts
function editUser(user: Readonly<{ name: string; meta: { age: number } }>) {
  user.name = "Changed"; // ❌ Error (TS stops this)
  user.meta.age = 99;    // ✅ Allowed! (nested object is still mutable)
}
```

- `Readonly` is **shallow** by default.
    
- If you want deep immutability, you need something like `ReadonlyDeep<T>` from utility libraries.
    

---

## **5. Default parameter traps**

When using object defaults, the same reference might be shared:

```ts
function addUser(user = { name: "Guest" }) {
  user.name = "Changed";
  return user;
}

let u1 = addUser();
let u2 = addUser();

console.log(u1 === u2); // ⚠ true in some cases if default is declared outside
```

- If you define the default object **outside** the function, all calls share it.
    

---

## **6. TypeScript’s type checking doesn’t prevent runtime issues**

Even if TypeScript says a function expects `{ name: string }`, you can still pass an object with missing properties using `as any`:

```ts
printUser({} as any); // ✅ Compiles, but crashes at runtime
```

---

### 🔹 Key Takeaways

- Objects in TS/JS are **mutable and passed by reference** — changes inside functions affect the caller.
    
- TypeScript’s `Readonly` is **shallow**.
    
- Excess property checks happen **only for inline literals**.
    
- Be careful with default parameter objects — they may be shared.
    
- TypeScript **only checks at compile time**; runtime mutations still happen.
    

---


# 🚀What is a Type Alias in TypeScript?

A **type alias** is like **giving a nickname** to a type so you can reuse it.  
Instead of writing a long type definition every time, you define it once and then use its short name.

📌 Think of it like saving someone’s phone number in your contacts —  
instead of dialing `+91-9847-123-456` every time, you just type `"Mom"`.

---

**Syntax:**

```ts
type AliasName = TypeDefinition;
```

---

## **2. Simple Example**

```ts
type UserName = string;

let name1: UserName = "Achyuth";
let name2: UserName = "Yadav";
```

Here:

- `UserName` is just another way of saying `string`.
    
- Makes the code **more readable**.
    

---

## **3. Why use Type Aliases? (Applications)**

✅ **Readability** → Your code explains itself.  
✅ **Reusability** → Define once, use many times.  
✅ **Complex Types** → Makes big types easy to handle.  
✅ **Consistency** → If you change a type in one place, it updates everywhere.

---

## **4. Real-Life Example**

Imagine you’re making an **eCommerce app**.

You have a product type:

```ts
type Product = {
  id: number;
  name: string;
  price: number;
  inStock: boolean;
};
```

Now, instead of rewriting `{ id: number; name: string; price: number; inStock: boolean }` everywhere, you just use:

```ts
function printProduct(product: Product) {
  console.log(`${product.name} - ₹${product.price}`);
}

const laptop: Product = {
  id: 1,
  name: "Gaming Laptop",
  price: 85000,
  inStock: true
};

printProduct(laptop);
```

✅ If you add a new property to `Product` later, every place using `Product` automatically updates.

---

## **5. Bonus: Type Alias for Union Types**

You can also use it for **multiple possible types**:

```ts
type ID = number | string;

let userId: ID;
userId = 101;   // ✅
userId = "A101"; // ✅
```

---

### Quick Analogy

📌 **Without type alias:**  
"Call me at `+91-9847-123-456`" (ugh, long).

📌 **With type alias:**  
"Call me at **Mom**" (short, clear, reusable).

---

# 🚀`readonly` and optional `?` in typescript
## **1. `readonly` in TypeScript**

### **What it is**

- `readonly` makes a property **immutable** after it’s been initialized.
    
- You can **set** the value when creating the object or inside the constructor (for classes), but you **cannot change** it later.
    

---

### **Syntax**

```ts
type User = {
  readonly id: number;
  name: string;
};

let user: User = { id: 101, name: "Achyuth" };

user.name = "Achy";    // ✅ allowed
user.id = 202;         // ❌ Error: Cannot assign to 'id' because it is a read-only property.
```

**In Classes**

```ts
class User {
  readonly id: number;
  name: string;

  constructor(id: number, name: string) {
    this.id = id; // ✅ can assign inside constructor
    this.name = name;
  }
}

const u = new User(1, "Achyuth");
u.name = "Achy";  // ✅
u.id = 2;         // ❌ Error
```

---

### **Where to use**

- For **IDs** or constants that should never change.
    
- For preventing accidental mutation of certain object fields.
    
- In API responses where some fields should remain fixed.
    

---

## **2. Optional Operator (`?`) in TypeScript**

### **Two Main Uses**

#### **a) Optional Property in Types**

Means the property **may or may not** exist.

```ts
type User = {
  id: number;
  name?: string; // optional
};

let user1: User = { id: 1 };
let user2: User = { id: 2, name: "Achyuth" };
```

---

#### **b) Optional Chaining (`?.`)**

Used to **safely access** nested properties **without causing an error** if something is `null` or `undefined`.

```ts
let user = { profile: { name: "Achyuth" } };
console.log(user.profile?.name); // "Achyuth"

let emptyUser = {};
console.log(emptyUser.profile?.name); // undefined (no error)
```

---

### **Application of `?`**

- Optional properties: When a field is **not always required**.
    
- Optional chaining: When accessing **deep nested objects** where a property might not exist (helps avoid `Cannot read property 'x' of undefined`).
    

---

## **Real-Life Example Combining `readonly` & Optional**

Imagine a **read-only `id`** (never changes) but an **optional `nickname`** (user may or may not have it):

```ts
type User = {
  readonly id: number; 
  name: string;
  nickname?: string; 
};

const u: User = { id: 101, name: "Achyuth" };

console.log(u.nickname?.toUpperCase()); // undefined (no error)
u.id = 202; // ❌ Error: Cannot assign to 'id'
```

---

# 🚀"combining types" in TypeScript
## **1. Union Types (`|`)**

- Means **"either this type or that type"**.
    
- The value can be **one of several** possible types.
    

```ts
type ID = number | string;

let userId: ID;

userId = 101;    // ✅ number
userId = "101";  // ✅ string
userId = true;   // ❌ Error
```

**Use case:**  
When a value can have multiple formats (e.g., an ID from DB could be number or string).

---

## **2. Intersection Types (`&`)**

- Means **"must have all properties of both types"**.
    
- Combines multiple types into **one** that contains everything.
    

```ts
type Person = { name: string };
type Employee = { employeeId: number };

type Staff = Person & Employee;

let worker: Staff = {
  name: "Achyuth",
  employeeId: 123
}; // ✅ must have BOTH name and employeeId
```

**Use case:**  
When you need a type that merges two concepts into one (like a person who is also an employee).

---

## **3. Using `type` + `&` or `|` for Complex Combos**

You can mix both unions and intersections.

```ts
type Admin = { role: "admin"; accessLevel: number };
type User = { role: "user"; points: number };

type Person = { name: string } & (Admin | User);

let a: Person = { name: "Achyuth", role: "admin", accessLevel: 5 }; // ✅
let u: Person = { name: "Yadav", role: "user", points: 10 };         // ✅
```

---

## **4. `extends` with Interfaces (for object types)**

Interfaces can **extend** each other to combine features.

```ts
interface Person {
  name: string;
}

interface Employee extends Person {
  employeeId: number;
}

const staff: Employee = {
  name: "Achyuth",
  employeeId: 123
};
```

**Use case:**  
When working with **object shapes** and you want reusability + hierarchy.

---

## **Summary Table**

|Method|Symbol|Meaning|Example|
|---|---|---|---|
|Union|`|`|**Either** type|
|Intersection|`&`|**Both** types|`{name:string} & {id:number}`|
|Interface `extends`|keyword|Inheritance for objects|`interface B extends A {}`|

---


# 🚀What are Array Types in TypeScript?

- In TypeScript, you can **specify the type** of elements an array can contain.
    
- This gives **type safety** — no pushing random stuff into the array by mistake.

    

---

## **2. Syntax**

You have **two main syntaxes**:

### **a) `type[]` Notation**

```ts
let numbers: number[] = [1, 2, 3];
numbers.push(4);    // ✅
numbers.push("hi"); // ❌ Error: Argument of type 'string' is not assignable to type 'number'
```

---

### **b) `Array<type>` Generic Notation**

```ts
let fruits: Array<string> = ["apple", "banana"];
fruits.push("mango"); // ✅
```

Both syntaxes do the same thing — **`number[]` is just shorthand for `Array<number>`**.

---

## **3. Special Array Type Variations**

### **a) Union Typed Arrays**

```ts
let mixed: (number | string)[] = [1, "two", 3, "four"];
```

---

### **b) Readonly Arrays**

```ts
const nums: readonly number[] = [1, 2, 3];
nums.push(4); // ❌ Cannot push into readonly array
```

**Use case:** When you don’t want the array to be mutated after creation.

---

### **c) Tuples (Fixed-Length Arrays)**

Tuples are a **special form of array** where you know exactly how many elements and what type each will be.

```ts
let person: [string, number] = ["Achyuth", 25];
// person = [25, "Achyuth"]; // ❌ wrong order
```

---

## **4. Use Cases**

- **Typed data lists**: e.g., list of product IDs (`number[]`).
    
- **Mixed but controlled lists**: e.g., (`(string | number)[]`).
    
- **Immutable collections**: `readonly string[]` for constant data.
    
- **Function parameters**: When you want a function to only accept an array of a certain type.
    

---

## **5. Application Example**

```ts
type Product = {
  id: number;
  name: string;
  price: number;
};

let products: Product[] = [
  { id: 1, name: "Shirt", price: 500 },
  { id: 2, name: "Pants", price: 900 }
];

// Function that only accepts Product[]
function printProducts(items: Product[]) {
  items.forEach(p => console.log(`${p.name} - ₹${p.price}`));
}

printProducts(products); // ✅
```

Here, the type ensures:

- Every item has the correct **shape**.
    
- You can’t push invalid data.
    

---


# 🚀What is a Union Type?

- A **union type** means a value can be **one of several types**.
    
- It uses the `|` (pipe) symbol.
    
- Example:
    
    ```ts
    let id: number | string;
    id = 101;    // ✅ number
    id = "101";  // ✅ string
    id = true;   // ❌ Error
    ```
    

---

## **2. Syntax**

```ts
type MyType = typeA | typeB | typeC;
```

**Examples:**

```ts
type ID = number | string;
type Status = "success" | "error" | "loading"; // union of string literals
```

---

## **3. Use Cases**

- **Flexible parameters**: A function can accept multiple types.
    
- **Multiple data formats**: IDs from a DB might be `number` or `string`.
    
- **Literal unions**: Restrict values to a fixed set of strings/numbers.
    

---

## **4. Example: Function with Union Type**

```ts
function printId(id: number | string) {
    if (typeof id === "string") {
        console.log(`ID in uppercase: ${id.toUpperCase()}`);
    } else {
        console.log(`ID doubled: ${id * 2}`);
    }
}

printId(101);     // ID doubled: 202
printId("achy");  // ID in uppercase: ACHY
```

Here **type narrowing** (checking `typeof`) helps TypeScript know exactly which type you’re dealing with.

---

## **5. Union with Arrays**

```ts
let values: (number | string)[] = [1, "two", 3];
```

This means **each element** can be number or string.

---

## **6. Literal Union Example**

```ts
type Direction = "up" | "down" | "left" | "right";

function move(dir: Direction) {
    console.log(`Moving ${dir}`);
}

move("up");     // ✅
move("forward"); // ❌ Error
```

Literal unions are **great for enums without extra runtime cost**.

---

If you want, I can give you **a single diagram** that shows the difference between **union types** and **intersection types** so you never mix them up during interviews.  
Want me to?