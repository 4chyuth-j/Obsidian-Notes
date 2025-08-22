# 🚀What is typescript?

**TypeScript** is a **superset of JavaScript** that adds **static typing** to the language.

### 🌟 In Simple Terms:

> TypeScript = JavaScript + Type Safety


### 🟦 What is TypeScript?

- **TypeScript (TS)** is a **superset of JavaScript**.  
    That means → it’s basically JavaScript **+ extra features**.
    
- The main extra feature is **static typing** → you can tell the compiler what type of data (string, number, boolean, etc.) you’re working with.
    
- TypeScript code **doesn’t run directly** in the browser or Node.js. It first **compiles down to normal JavaScript**, then runs.
    

---

### 🔑 Why use TypeScript?

- ✅ **Catches errors early** → If you try to add a number and a string, TS will warn you before running.
    
- ✅ **Better code readability** → You can see what type of data a function expects or returns.
    
- ✅ **Great for big projects** → Helps teams avoid silly bugs.
    
- ✅ **Supports modern JS features** → Classes, interfaces, async/await, etc.
---

### 🧠 Why Use TypeScript example?

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
### 🔄 What is Compilation in TypeScript?

- When you write **TypeScript (TS)** code, the computer **can’t run it directly** (neither Node.js nor browsers understand TypeScript).
    
- So your code goes through a process called **compilation** → which converts TypeScript (`.ts`) files into plain JavaScript (`.js`) files.
    
- After that, the JavaScript code is what actually runs.

### 🔑 Why compilation is important in TS?

- Checks your code for errors before it even runs.
    
- Converts TypeScript’s extra features (types, interfaces, generics, etc.) into plain JavaScript.
    
- Ensures compatibility → because browsers only understand JS, not TS.


# 🚀 Compilation vs Transpilation

## 🟦 Compilation

- General meaning = **taking code written in one language and converting it into another language** (usually lower-level, machine-readable).
    
- In **TypeScript**, compilation = converting `.ts` → `.js`.
    
- Example:
    
    - You write `app.ts` → TypeScript compiler (`tsc`) → produces `app.js` → Node.js/browser runs it.
        

So: **TypeScript Compilation = High-level TS → High-level JS** (not directly machine code, but another language that runtime understands).

---

## 🟩 Transpilation

- Transpilation = **translation between two versions or flavors of the _same_ language level**.
    
- It usually means converting **modern JavaScript (ES6/ES7)** into **older JavaScript (ES5)** that older browsers can understand.
    
- Example: Using **Babel** to convert:
    

**Modern JS (ES6):**

```js
const greet = (name) => `Hello, ${name}`;
```

**Transpiled to ES5:**

```js
var greet = function(name) {
  return "Hello, " + name;
};
```

---

## 🆚 Key Difference

- **Compilation** → Different languages (TS → JS, C++ → Machine Code).
    
- **Transpilation** → Same family/language, just different **versions or syntax levels** (ES6 → ES5).
    

---

### ⚡ Real-World Example in a Project

- You write code in **TypeScript (TS)**.
    
- TypeScript compiler **compiles** it into JavaScript.
    
- Then, if you want older browser support, Babel **transpiles** that JavaScript into ES5.
    

So pipeline could be:  
`TS (.ts) → (compile) → JS (ES6) → (transpile) → JS (ES5)`

---

👉 In short,

- **Compilation = different languages**
    
- **Transpilation = same language, different versions**
    

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
# 🚀What is Type assertion

https://www.geeksforgeeks.org/typescript/explain-type-assertions-in-typescript/

## 🟢 What is Type Assertion?

- **Type Assertion** tells TypeScript:  
    👉 “Hey compiler, trust me — I know the type better than you do.”
    
- It doesn’t **change the actual value** at runtime, it just **informs TypeScript** about the type.
    
- Similar to **type casting** in other languages (like C/C++/Java), but only affects **TypeScript’s type system**, not the actual code execution.
    

---

## 📝 Syntax

There are **two ways**:

1. **Angle-bracket syntax**
    

```ts
let value: unknown = "hello";
let strLength: number = (<string>value).length;
```

2. **`as` syntax** (recommended, especially in React/JSX projects)
    

```ts
let value: unknown = "hello";
let strLength: number = (value as string).length;
```

---

## ⚡ Example

```ts
let someValue: unknown = "Achyuth";

// ❌ Without assertion → Error
// console.log(someValue.length);

// ✅ With assertion
console.log((someValue as string).length); // 7
```

Here, we told TypeScript: "Treat `someValue` as a `string` so I can access `.length`."

---

## 🚨 Important Notes

- **No runtime effect** → it doesn’t convert the value, only tells TS to assume a type.
    
- **Dangerous if used wrong** → if you lie to TypeScript, you can still crash your program.
    

Example:

```ts
let num: any = 100;
let str = num as string;  // TS thinks it's a string
console.log(str.toUpperCase()); // Runtime Error ❌
```

---

## 🆚 Type Assertion vs Type Casting

- **Type Assertion (TS)** → only changes how the **compiler sees the type**.
    
- **Type Casting (other langs)** → actually converts the value (like `int → float`).
    

In TS, **type assertion doesn’t actually convert values**.

---

✅ **Summary:**  
Type Assertion = “I know better than the compiler, treat this value as this type.”

---

Do you want me to also show you **when to use type assertion vs when to use type guards (`typeof`, `instanceof`)**?
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

# 🚀 `any` vs `unknown` type

**More verbosely, `unknown` is _I don't know (yet), thus I have to figure it out_, `any` is _I don't care, thus I don't care_
## 🟠 `any`

- `any` means: **“turn off type checking.”**
    
- You can assign it to anything, and use it as anything.
    
- TypeScript won’t complain — but you lose all safety.
    

### Example:

```ts
let value: any;

value = 10;
value = "hello";
value = true;

// Dangerous 😅
value.toUpperCase();  // ✅ Compiles, but may crash at runtime if value isn’t string
```

👉 **Use case:** quick prototyping, migrating old JS code, or when you don’t know the type yet.  
👉 **Downside:** no protection from bugs.

---

## 🟢 `unknown`

- `unknown` also means: **“it could be anything”**
    
- BUT, unlike `any`, you **can’t directly use it**.
    
- You must **check** the type first (type narrowing).
    

### Example:

```ts
let data: unknown;

data = 10;
data = "hello";

// ❌ Error: TS doesn’t know if data is string
// data.toUpperCase();

// ✅ Safe usage with type check
if (typeof data === "string") {
  console.log(data.toUpperCase()); 
}
```

👉 **Use case:** when you’re dealing with **external data** (API, user input, DB), and you want TypeScript to force you to check the type first.  
👉 **Safer** than `any`.

---

## 🆚 `any` vs `unknown`

|Feature|`any` 🚨|`unknown` ✅|
|---|---|---|
|Can hold anything?|Yes|Yes|
|Type safety|❌ None|✅ Must check before use|
|Good for|Quick hacks, legacy JS|External data, safer coding|
|Example use|`let x: any`|`let y: unknown`|

---

### ⚡ Analogy

- `any` = "I’ll drive **blindfolded** 🚗💥"
    
- `unknown` = "I’ll drive, but only **after checking the road** 🚦✅"
    

---

✅ **Summary:**

- Use `any` when you want to **skip type checking** completely.
    
- Use `unknown` when you **don’t know the type yet, but want to keep safety**.
    

---

# 🚀`void` vs `never` type


## 🟢 `void`

- Means: **function doesn’t return anything** (or returns `undefined`).
    
- It’s like saying: “This function finishes, but I don’t care about its result.”
    

### Example:

```ts
function logMessage(message: string): void {
  console.log(message);
}

let result = logMessage("Hello"); 
// result is of type void (actually undefined at runtime)
```

👉 Used for **functions that only do side effects** (like logging, updating DB, etc).

---

## 🔴 `never`

- Means: **function never successfully finishes / returns**.
    
- Two common cases:
    
    1. Function **always throws an error**
        
    2. Function **never ends** (infinite loop)
        

### Example 1: Function that throws

```ts
function throwError(msg: string): never {
  throw new Error(msg);
}
```

### Example 2: Infinite loop

```ts
function infiniteLoop(): never {
  while (true) {
    console.log("Running...");
  }
}
```

👉 Used for **functions that truly never give back control**.

---

## 🆚 Difference Table

|Feature|`void` 🟢|`never` 🔴|
|---|---|---|
|Returns?|No useful value (implicitly `undefined`)|Never returns at all|
|Example use|Logging, side effects|Errors, infinite loops|
|Function ends normally?|✅ Yes|❌ No|
|At runtime|`undefined`|Nothing, function never finishes|

---

## ⚡ Analogy

- `void` = "I’ll finish the task, but won’t give you anything back."
    
- `never` = "I’ll **never** finish the task at all."
    

---

✅ **Summary**

- **`void`** → function executes but doesn’t return anything.
    
- **`never`** → function never completes (error or infinite loop).
    

---

# 🚀 `const` vs `readonly` 

## 🟢 `const`

- **Used with variables.**
    
- Means: the variable **cannot be reassigned** after declaration.
    
- BUT → the contents (if it’s an object/array) can still be changed.
    

### Example:

```ts
const x = 10;
// x = 20; ❌ Error: cannot reassign

const arr = [1, 2, 3];
arr.push(4); // ✅ Allowed, because array contents can change
```

👉 `const` = **binding (variable reference) is fixed**, but object/array contents are still mutable.

---

## 🔵 `readonly`

- **Used with properties of objects, classes, arrays, and tuples.**
    
- Means: the **property itself cannot be reassigned** after initialization.
    

### Example:

```ts
type User = {
  readonly id: number;
  name: string;
};

const user: User = { id: 1, name: "Achyuth" };

user.name = "Rahul"; // ✅ Allowed
// user.id = 2; ❌ Error: cannot assign to readonly property
```

👉 `readonly` = **property cannot be changed after it’s set once**.

---

## ⚡ Combined Example

```ts
const numbers: readonly number[] = [1, 2, 3];

// numbers.push(4); ❌ Error: readonly array
// numbers[0] = 10; ❌ Error: cannot modify

console.log(numbers[0]); // ✅ Reading is allowed
```

---

## 🆚 Difference Table

|Feature|`const` 🟢|`readonly` 🔵|
|---|---|---|
|Applies to|Variables|Properties (objects, classes, arrays, tuples)|
|Prevents reassignment|✅ Yes|✅ Yes (for that property)|
|Prevents mutation|❌ No|✅ Yes|
|Example use|`const x = 10;`|`readonly id: number;`|

---

## ⚡ Analogy

- `const` = "You can’t **move the box** somewhere else, but you can still **change what’s inside**." 📦
    
- `readonly` = "You can **open the box and look**, but you can’t **change what’s inside**." 🔒
    

---

✅ **Summary**

- **`const`** → for variables, stops reassignment.
    
- **`readonly`** → for object/array/class properties, stops modification.
    

---

Want me to also show you a **real-world example** where we use both `const` and `readonly` together (like in an `enum` or config object)?
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


# 🚀What is a Tuple? 

- A **tuple** is like an array, but it has a **fixed length** and **known types for each index**.
    
- You can control:
    
    - How many elements it has.
        
    - What type each element is.
        
    - The order of those elements.
        

---

## **2. Syntax**

```ts
let myTuple: [string, number];

myTuple = ["Achyuth", 25]; // ✅
myTuple = [25, "Achyuth"]; // ❌ Order matters
myTuple = ["Achyuth"];     // ❌ Missing element
```

---

## **3. Why Tuples Exist**

Arrays are flexible but sometimes **too flexible**.  
Example:

```ts
let person: (string | number)[] = ["Achyuth", 25, "extra"]; // This is allowed but maybe not intended
```

Tuples let you **lock the structure** so mistakes are caught at compile time.

---

## **4. Real-Life Use Cases**

1. **Coordinates / fixed values**
    
    ```ts
    type Point = [number, number];
    let p: Point = [10, 20];
    ```
    
2. **API responses**
    
    ```ts
    type ApiResponse = [number, string]; // [statusCode, message]
    const res: ApiResponse = [200, "OK"];
    ```
    
3. **Key-value pairs**
    
    ```ts
    type KeyValue = [string, string];
    let entry: KeyValue = ["username", "Achyuth"];
    ```
    

---

## **5. Optional Tuple Elements**

You can make some tuple elements optional:

```ts
let data: [string, number?];
data = ["hello"];       // ✅
data = ["hello", 123];  // ✅
```

---

## **6. Readonly Tuples**

Prevent modification:

```ts
const coords: readonly [number, number] = [10, 20];
// coords[0] = 50; // ❌ Error
```

---

## **7. Destructuring Tuples**

```ts
let user: [string, number] = ["Achyuth", 25];
const [name, age] = user;
console.log(name); // "Achyuth"
console.log(age);  // 25
```

---



# 🚀What is an Enum?

- An **enum** (short for “enumeration”) is a way to define a set of **named constants**.
    
- Improves code readability and reduces "magic numbers" or random strings.
    
- Enums exist **only in TypeScript** (not plain JS), but compile down to JS objects.
    

**Enums in TypeScript are a way to define a set of named constants that represent related values.**  
They make the code more readable and help avoid using "magic strings" or arbitrary numbers.  
Enums can be numeric or string-based, and they ensure type safety by restricting a variable to only those predefined values.

---

## **2. Enum Syntax**

### **a) Numeric Enum (default)**

```ts
enum Direction {
  Up,      // 0
  Down,    // 1
  Left,    // 2
  Right    // 3
}

let move: Direction = Direction.Up;
console.log(move); // 0
console.log(Direction[0]); // "Up" (reverse mapping)
```

By default, the first member starts at `0` and increments by `1`.

---

### **b) Custom Numeric Enum**

```ts
enum Direction {
  Up = 1,
  Down = 5,
  Left,   // 6
  Right   // 7
}
```

You can set the starting number or even set each one manually.

---

### **c) String Enum**

```ts
enum Direction {
  Up = "UP",
  Down = "DOWN",
  Left = "LEFT",
  Right = "RIGHT"
}

console.log(Direction.Up); // "UP"
```

- No reverse mapping for string enums (because multiple keys can have the same string value).
    
- More readable in logs and debugging.
    

---

### **d) Heterogeneous Enum** (Mix of string & number)

> Rarely recommended (confusing to maintain)

```ts
enum Mixed {
  No = 0,
  Yes = "YES"
}
```

---

## **3. Reverse Mapping**

Only **numeric enums** have reverse mapping:

```ts
enum Status {
  Success = 1,
  Error = 2
}

console.log(Status.Success); // 1
console.log(Status[1]);      // "Success"
```

---

## **4. Const Enums (Compile-time Optimization)**

- **`const enum`** completely removes the object at compile time.
    
- Replaces enum values directly in your code → smaller & faster JS.
    

```ts
const enum Direction {
  Up,
  Down
}

let dir = Direction.Up; // Compiles to: var dir = 0;
```

⚠️ **Note:** `const enum` can’t have computed members.

---

## **5. Computed & Constant Members**

```ts
enum FileAccess {
  None,               // 0
  Read = 1 << 1,       // 2
  Write = 1 << 2,      // 4
  ReadWrite = Read | Write, // 6
  Length = "123".length // computed
}
```

---

## **6. Why Use Enums?**

- **Code clarity**: Instead of `move("UP")`, you can `move(Direction.Up)`.
    
- **Refactoring safety**: Changing `"UP"` in one place updates everywhere.
    
- **Type safety**: Prevents invalid values.
    

---

## **7. Enum vs Union of Literals**

Modern TypeScript often prefers **literal unions** over enums for flexibility:

```ts
type Direction = "UP" | "DOWN" | "LEFT" | "RIGHT";

function move(dir: Direction) {}
move("UP"); // ✅
move("SIDE"); // ❌
```

- Unions are simpler, have no runtime cost, and work better with string-based values.
    
- But enums are still good when:
    
    - You need **numeric values**.
        
    - You want **reverse mapping**.
        
    - You have **bitwise flags**.
        

---

## **8. Real-Life Example**

```ts
enum UserRole {
  Admin = "ADMIN",
  User = "USER",
  Guest = "GUEST"
}

interface User {
  name: string;
  role: UserRole;
}

const u: User = { name: "Achyuth", role: UserRole.Admin };

if (u.role === UserRole.Admin) {
  console.log("Access granted to admin panel");
}
```

---


# 🚀What is an `interface`?

>**An interface in TypeScript is a way to define the shape of an object.**  
   It specifies what properties and methods an object should have, along with their types, without providing implementation.  
   Interfaces support **type-checking** at compile-time and help enforce contracts in your code.

An `interface` in TypeScript **describes the shape (contract) of a value** — usually objects. It’s a compile-time tool: it helps TypeScript check that values have the properties/methods you expect. **Interfaces disappear at runtime** (they don’t produce JS code).

Think: _“If something quacks like this interface, TypeScript will accept it.”_ — structural (duck) typing.

## Basic syntax & examples

```ts
interface User {
  id: number;
  name: string;
  age?: number;           // optional
  readonly createdAt: Date; // cannot be changed after initialization
  greet(): void;          // method signature
}

// use it
const u: User = {
  id: 1,
  name: "Achyuth",
  createdAt: new Date(),
  greet() { console.log("hi"); }
};
```

## Common interface features

- **Optional properties**: `prop?: Type` — may be missing.
    
- **Readonly**: `readonly prop: Type` — cannot reassign.
    
- **Method signatures**: `doIt(x: number): boolean`.
    
- **Index signatures**: describe dynamic keys.
    
    ```ts
    interface StringMap { [key: string]: string }
    interface NumArray { [index: number]: string } // like array of strings
    ```
    
- **Call signatures** (function types):
    
    ```ts
    interface Adder { (a: number, b: number): number }
    const add: Adder = (x,y) => x+y;
    ```
    
- **Hybrid types** (callable object with properties):
    
    ```ts
    interface Counter {
      (start: number): string;
      interval: number;
      reset(): void;
    }
    ```
    
- **Extending**: compose interfaces.
    
    ```ts
    interface Employee extends User { employeeId: number }
    ```
    

## Interfaces with classes

Classes can **implement** interfaces (enforce contract):

```ts
interface Logger { log(msg: string): void }

class ConsoleLogger implements Logger {
  log(msg: string) { console.log(msg) }
}
```

`implements` only checks types at compile-time — no runtime effect.

## Generics with interfaces

Make interfaces flexible:

```ts
interface ApiResponse<T> {
  data: T;
  status: number;
  error?: string;
}

const resp: ApiResponse<User[]> = { data: [u], status: 200 };
```

## Interface vs `type` — short and useful comparison

- `interface` — great for **object shapes**, can be **extended** and **merged** (declaration merging).
    
- `type` — more flexible: can create **unions, intersections, mapped types, tuples**, aliases of primitives, etc.
    
- You **can** often use either for object shapes; many style guides prefer `interface` for objects and `type` for unions/complex types.
    

Example where `type` is necessary:

```ts
type ID = string | number; // can't use interface for union
```

## Declaration merging (unique to interfaces)

You can declare an interface twice and TypeScript merges them:

```ts
interface Window { debug?: boolean }
interface Window { myLib?: any }
// now Window has both properties
```

Useful for augmenting libs, but can be confusing if overused.

## Excess property checks & structural typing gotchas

- If you assign an **object literal** with extra props, TypeScript may warn:
    
    ```ts
    const u: User = { id:1, name:"a", extra: true } // error
    ```
    
    But if you assign first to a variable, extra props allowed (structural typing).
    
- Structural typing means any object with required props is assignable — watch accidental matches.
    

## When to use interfaces (practical cases)

- Define shapes of **API responses / DTOs**.
    
- Public **library API** contracts.
    
- Class **contracts** (e.g., service interfaces for DI).
    
- Function parameter types when expecting object shapes.
    
- `.d.ts` ambient declarations to describe third-party libs.
    

## Best practices & tips

- Prefer `readonly` for things that shouldn't change (IDs, timestamps).
    
- Use optional (`?`) when property is truly optional — don’t overuse.
    
- Avoid wide `any` index signatures; prefer conservative types.
    
- Use `type` for unions/tuples or when you need advanced type operators.
    
- Keep interfaces small and single-purpose where possible.
    

## Small exercises (try these)

1. Create `interface Product { id:number; title:string; price:number; tags?:string[] }` and a function `calculateTotal(products: Product[]): number`.
    
2. Make `interface Service<T> { get(id:number): Promise<T> }` and implement in a class.
    
3. Write a hybrid interface for a function that also has `count` property and `reset()`.
    

---

# 🚀`Interface` explanation
Nah Achyuth, **interfaces are not just for creating objects** — that’s a common beginner misunderstanding.

While the **most common** use is to describe the _shape of an object_, TypeScript interfaces can also define:

---

## **1. Object Shapes** _(the usual way)_

```ts
interface User {
  id: number;
  name: string;
}
```

---

## **2. Function Types**

An interface can describe **call signatures** (functions).

```ts
interface Add {
  (a: number, b: number): number;
}

const sum: Add = (x, y) => x + y;
```

---

## **3. Class Contracts**

Interfaces can be used to **enforce** that a class implements certain methods/properties.

```ts
interface Logger {
  log(message: string): void;
}

class ConsoleLogger implements Logger {
  log(message: string) {
    console.log(message);
  }
}
```

---

## **4. Indexable Types**

They can describe how something can be **indexed**, like arrays or objects with dynamic keys.

```ts
interface StringArray {
  [index: number]: string;
}

let arr: StringArray = ["a", "b", "c"];
```

---

## **5. Hybrid Types**

Objects that are **both callable and have properties**.

```ts
interface Counter {
  (): void;         // callable
  count: number;    // property
}

const counter = (() => {
  counter.count++;
}) as Counter;

counter.count = 0;
counter(); // increments
```

---

## **6. Generics**

Interfaces can be **generic**, meaning they work with multiple types.

```ts
interface ApiResponse<T> {
  data: T;
  status: number;
}

const userResponse: ApiResponse<{ id: number; name: string }> = {
  data: { id: 1, name: "Achyuth" },
  status: 200
};
```

---

✅ **So in short:**  
Interfaces are a **blueprint for any shape** — objects, functions, classes, arrays, even weird hybrid types. They’re not just for “making objects” but for _describing how something should look or behave_.

---

# 🚀**Type vs Interface**
## **1. What They Have in Common**

Both **`type`** and **`interface`** can:

- Describe **object shapes**
    
- Describe **function signatures**
    
- Use **generics**
    
- Be **extended/combined** (with some differences)
    
- Be used for **type checking** at compile time
    

Example (both valid):

```ts
type UserType = { id: number; name: string };
interface UserInterface { id: number; name: string }
```

---

## **2. Key Differences**

|Feature|**Interface**|**Type Alias**|
|---|---|---|
|**Primary Use**|Describing object/class shapes|Can describe any type (primitives, unions, tuples, etc.)|
|**Extension**|`extends` keyword|Intersections with `&`|
|**Declaration Merging**|✅ Can merge multiple declarations|❌ Cannot merge once declared|
|**Runtime**|No runtime code (only TS)|No runtime code (only TS)|
|**Unions**|❌ Cannot directly create unions|✅ Can make unions (`type A = B \| C`)|
|**Tuples**|❌ Not ideal for tuples|✅ Can easily define tuples|
|**Primitives**|❌ Cannot alias primitive directly|✅ Can alias primitive: `type ID = number`|

---

## **3. Examples**

### **a) Interface — Object Contract**

```ts
interface User {
  id: number;
  name: string;
}

interface Admin extends User {
  role: "admin";
}
```

---

### **b) Type — Flexible**

```ts
type ID = number | string; // primitive + union
type Point = [number, number]; // tuple

type User = {
  id: ID;
  name: string;
};
```

---

### **c) Extending**

```ts
// Interface extending interface
interface A { a: number }
interface B extends A { b: number }

// Type extending type (intersection)
type AType = { a: number }
type BType = AType & { b: number }
```

---

### **d) Declaration Merging**

```ts
interface Box { width: number }
interface Box { height: number }

// Box now has both width and height
```

`type` ❌ — you can’t redeclare and merge.

---

## **4. When to Use Which**

💡 **Use `interface` when:**

- You are defining the shape of **objects or classes**.
    
- You want **declaration merging** (good for library augmentation).
    
- You need to ensure **class implements** a contract.
    

💡 **Use `type` when:**

- You need **union** or **intersection** types.
    
- You want to alias **primitives**, **tuples**, or **function types**.
    
- You want advanced type features (`keyof`, `mapped types`, etc.).
    

---

## **5. Quick Rule of Thumb**

- **Interfaces** = Blueprints for **objects/classes** (extendable & mergeable).
    
- **Types** = More **flexible**, can do everything except merging, good for unions & primitives.
    

---


# 🚀Generics 

## **Definition of Generics**

> **Generics** in TypeScript are a way to create reusable components (functions, classes, interfaces) that work with **multiple types** while still maintaining **type safety**.  
> They act like **type variables** — placeholders for actual types — which get replaced when the component is used.

Think of generics as _“write once, work for any type, but stay strongly typed”_.

In short:

> Generics here are like **placeholders for types** that get filled in when you call the function, keeping your code **flexible but type-safe**.

---

## **Why use Generics?**

1. **Reusability** — one function or class can handle different types without rewriting code.
    
2. **Type Safety** — TypeScript checks that you only use the correct type in every place.
    
3. **Better Autocomplete & Inference** — editors like VS Code can predict the correct type for you.
    
4. **Avoids `any`** — unlike `any`, generics preserve the connection between input and output types.
    

---

## **Usage Examples**

### **1. Generic Function**

```ts
function identity<T>(value: T): T {
  return value;
}

const num = identity<number>(42);    // T is number → returns number
const str = identity<string>("hi");  // T is string → returns string
```

- Same function works for `number`, `string`, or any type.
    
- Type is locked to whatever you pass in.
    

---

### **2. Generic with Interfaces**

```ts
interface Box<T> {
  contents: T;
}

const numberBox: Box<number> = { contents: 100 };
const stringBox: Box<string> = { contents: "Hello" };
```

- `Box<T>` can store _any type_, but once chosen, it's fixed for that instance.
    

---

### **3. Generic in Arrays**

```ts
const numbers: Array<number> = [1, 2, 3];
const names: Array<string> = ["Alice", "Bob"];
```

- `Array<T>` is a built-in generic type.
    
- Here, `T` is `number` in the first case, `string` in the second.
    

---

### **4. Generic in Classes**

```ts
class DataStore<T> {
  private data: T[] = [];
  
  add(item: T) {
    this.data.push(item);
  }

  getAll(): T[] {
    return this.data;
  }
}

const stringStore = new DataStore<string>();
stringStore.add("Hi");

const numberStore = new DataStore<number>();
numberStore.add(42);
```

- `DataStore<T>` works for `string`, `number`, or any custom type.
    

---

### **5. Generics with Constraints**

You can limit what types are allowed.

```ts
function printLength<T extends { length: number }>(value: T): number {
  return value.length;
}

printLength("hello"); // ✅ Works (string has length)
printLength([1, 2, 3]); // ✅ Works (array has length)
printLength(42); // ❌ Error (number has no length)
```

---

# 🚀Generics in `array` and `arrow function`

## **1. Generics with Arrays**

In TypeScript, you can declare arrays in two main ways:

### **A. Shorthand syntax**

```ts
const numbers: number[] = [1, 2, 3];
const strings: string[] = ["a", "b", "c"];
```

Here, the type is fixed — `number[]` means only numbers, `string[]` means only strings.

---

### **B. Generic Array type**

```ts
const numbers: Array<number> = [1, 2, 3];
const strings: Array<string> = ["a", "b", "c"];
```

- `Array<number>` is the **generic form**.
    
- `Array<T>` says: _"This is an array of T"_, where `T` is a type parameter.
    
- This form is useful when you work with **complex or custom types**:
    

```ts
interface Bottle {
  color: string;
  size: number;
}

const bottles: Array<Bottle> = [
  { color: "blue", size: 1 },
  { color: "green", size: 2 },
];
```

---

## **2. Generics in Arrow Functions**

You can also write **arrow functions** with generics:

### **Example:**

```ts
// Generic arrow function
const getFirstElement = <T>(arr: T[]): T => {
    return arr[0];
};
```

- `<T>` — the generic type parameter.
    
- `(arr: T[])` — array of type `T`.
    
- `: T` — returns the same type as the array’s element type.
    

---

### **Usage:**

```ts
const firstNum = getFirstElement<number>([10, 20, 30]); 
// T = number → returns number

const firstString = getFirstElement<string>(["a", "b", "c"]); 
// T = string → returns string

const firstBottle = getFirstElement<Bottle>([
  { color: "blue", size: 1 },
  { color: "red", size: 2 }
]);
// T = Bottle → returns Bottle
```

---

### **Type Inference (no need to explicitly pass `<T>` sometimes)**

```ts
const first = getFirstElement([100, 200, 300]); // T is inferred as number
```

TypeScript figures out `T` from the argument you pass.

---

✅ **Why use this?**

- **Reusability:** One arrow function works for `number[]`, `string[]`, custom objects, etc.
    
- **Type Safety:** If you pass an array of `User` objects, you’re guaranteed to get a `User` back — not something random.
    

---

# 🚀 Generics with Constraints


## **1. Recap: What’s a generic without constraints?**

Normally, a generic like:

```ts
function identity<T>(value: T): T {
    return value;
}
```

means **T can be any type** — primitive, object, array, union, etc.

---

## **2. What’s a constraint?**

A **constraint** limits what types can be passed for `T`.

We do this with `extends`:

```ts
function process<T extends SomeType>(value: T): T {
    return value;
}
```

Here:

- `T extends SomeType` means "T must be SomeType **or a subtype of it**".
    
- You **cannot** pass types that don’t satisfy the constraint.
    

---

## **3. Example 1 — Constraining to objects with a certain shape**

```ts
function getLength<T extends { length: number }>(value: T): number {
    return value.length;
}
```

✅ Works:

```ts
getLength("Hello");               // string has length
getLength([1, 2, 3]);              // array has length
getLength({ length: 10 });         // object with length
```

❌ Error:

```ts
getLength(42); // number doesn’t have a length property
```

---

## **4. Example 2 — Constraining to an interface**

```ts
interface HasId {
    id: number;
}

function printId<T extends HasId>(obj: T) {
    console.log(obj.id);
}
```

✅ Works:

```ts
printId({ id: 1, name: "Achu" });
printId({ id: 99 });
```

❌ Error:

```ts
printId({ name: "Achu" }); // no `id` property
```

---

## **5. Example 3 — Constraining to multiple things**

We can combine constraints with `&` (intersection types):

```ts
function mergeAndCount<T extends object & { length: number }>(obj: T) {
    console.log(obj.length);
}
```

Here `T` must:

1. Be an object (`object`)
    
2. Have a `length` property (`{ length: number }`)
    

---

## **6. Example 4 — Using constraints with arrays**

```ts
function getFirst<T extends number | string>(arr: T[]): T {
    return arr[0];
}
```

- Now the array must contain only numbers or strings.
    
- No booleans, objects, etc.
    

✅ Works:

```ts
getFirst(["apple", "banana"]);
getFirst([1, 2, 3]);
```

❌ Error:

```ts
getFirst([true, false]); // boolean not allowed
```

---

## **Why use constraints?**

- Without them, generics are **too open** — you lose safety when you rely on specific properties.
    
- Constraints **give you the best of both worlds**:
    
    - Still flexible (can accept many different types)
        
    - Still safe (rejects types that don’t meet the requirements)
        

---

# 🚀Generics Classes

## **1. What is a Generic Class?**

A **generic class** is just like a normal class, **but it can work with different types while still being type-safe**.

- You add a **type parameter** (`<T>`) to the class definition.
    
- Anywhere you use `T` inside the class, it will be replaced by the **actual type** when you create an object.
    

---

## **2. Syntax**

```ts
class Box<T> {
    content: T;

    constructor(value: T) {
        this.content = value;
    }

    getContent(): T {
        return this.content;
    }
}
```

- `T` is a placeholder for a type.
    
- It gets decided **when you create an instance**.
    

---

## **3. Usage**

```ts
const stringBox = new Box<string>("Hello");
console.log(stringBox.getContent()); // "Hello" (type: string)

const numberBox = new Box<number>(42);
console.log(numberBox.getContent()); // 42 (type: number)
```

Here:

- `Box<string>` means `T` = `string`
    
- `Box<number>` means `T` = `number`
    

---

## **4. With Constraints**

You can also **restrict** what type `T` can be using `extends`:

```ts
class Collection<T extends { id: number }> {
    items: T[] = [];

    add(item: T) {
        this.items.push(item);
    }
}
```

✅ Works:

```ts
const users = new Collection<{ id: number; name: string }>();
users.add({ id: 1, name: "Achu" });
```

❌ Error:

```ts
users.add({ name: "No ID" }); // missing id
```

---

## **5. Real-World Example**

```ts
interface Product {
    id: number;
    name: string;
}

class DataStore<T> {
    private store: T[] = [];

    addItem(item: T) {
        this.store.push(item);
    }

    getItems(): T[] {
        return this.store;
    }
}

// Storing Products
const productStore = new DataStore<Product>();
productStore.addItem({ id: 1, name: "Laptop" });
productStore.addItem({ id: 2, name: "Phone" });

console.log(productStore.getItems());
```

Here:

- The same `DataStore` class could be reused for `Product`, `User`, `Order`, etc., **without losing type safety**.
    

---

## **Why Generic Classes?**

- **Reusability:** One class can handle multiple data types without rewriting it.
    
- **Type Safety:** The compiler ensures you only put the right type of data inside.
    
- **Scalability:** Useful in data structures, storage services, or utility classes.
    

---

## ⚠️💀 Note:-- regarding Type specification during calls
Not always.  
When you make a **generic class**, mentioning the type at the call (like `new Box<string>("Hello")`) is **optional** — TypeScript can often figure it out (**type inference**).

---

## **1. With explicit type**

```ts
class Box<T> {
    content: T;
    constructor(value: T) {
        this.content = value;
    }
}

const stringBox = new Box<string>("Hello"); // Explicit
```

- Here, you **manually** tell TypeScript: "`T` is `string`".
    
- This is useful when:
    
    - You want to be extra clear.
        
    - The type cannot be guessed from the constructor arguments.
        
    - You want a **wider or more specific** type than inference would give.
        

---

## **2. With inferred type**

```ts
const inferredBox = new Box("Hello"); // T is automatically string
```

- TypeScript sees `"Hello"` is a string → infers `T = string`.
    
- Less typing, cleaner code.
    

---

## **3. When you must specify the type**

Sometimes TypeScript **can’t guess** the type — for example:

```ts
const emptyBox = new Box<string>(""); // Required, because "" alone isn’t enough for inference
```

Or when the constructor doesn’t take any arguments:

```ts
class DataStore<T> {
    items: T[] = [];
}

const store = new DataStore<number>(); // Must specify number, nothing to infer from
```

---

✅ **Rule of thumb**

- **If the type can be inferred** → let TS figure it out.
    
- **If it can’t be inferred or you need a specific constraint** → pass it explicitly.
    

---

# 🚀Type narrowing


## **1. What is Type Narrowing?**

In TypeScript, **type narrowing** means:

> Starting with a variable that could be **multiple types**, and then writing code that makes TypeScript “narrow” it down to a more specific type in certain parts of the code.

It’s TypeScript’s way of saying:  
_"Okay, I know this could be `string | number`, but right here in this `if` block, I know for sure it’s a `string`."_

---

## **2. Why it’s needed**

If you have a union type:

```ts
let value: string | number;
```

TS doesn’t let you directly use `string`-only or `number`-only features until it knows **exactly** which one it is.

Example:

```ts
value.toUpperCase(); // ❌ Error — value might not be string
```

---

## **3. How Type Narrowing Works**

We “narrow” the type using **checks**.

---

### **A. `typeof` check**

```ts
function printValue(val: string | number) {
    if (typeof val === "string") {
        // val is now string here
        console.log(val.toUpperCase());
    } else {
        // val is now number here
        console.log(val.toFixed(2));
    }
}
```

---

### **B. Equality check**

```ts
function process(id: string | null) {
    if (id !== null) {
        // id is now string here
        console.log(id.toUpperCase());
    }
}
```

---

### **C. `instanceof` check**

```ts
class Dog {
    bark() {}
}
class Cat {
    meow() {}
}

function speak(animal: Dog | Cat) {
    if (animal instanceof Dog) {
        animal.bark(); // Dog only
    } else {
        animal.meow(); // Cat only
    }
}
```

---

### **D. Property check (`in` keyword)**

```ts
type Fish = { swim: () => void };
type Bird = { fly: () => void };

function move(animal: Fish | Bird) {
    if ("swim" in animal) {
        animal.swim(); // Fish
    } else {
        animal.fly(); // Bird
    }
}
```

---

## **4. Why it’s Useful**

- **Type safety** → avoids runtime errors from calling wrong methods.
    
- **Better IntelliSense** → TS will auto-suggest methods for the narrowed type.
    
- **Cleaner code** → you don’t have to manually cast types everywhere.
    

---

## **5. Real-life analogy**

Imagine you have a box labeled **"Fruit or Vegetable"**.  
Before you slice it, you check:

- If it’s an apple → you use a fruit knife.
    
- If it’s a carrot → you use a vegetable peeler.
    

That check is **narrowing**.

---
# 🚀 What is type guard?


👉 A **Type Guard** is a technique (or expression) used to **narrow down the type** of a variable within a conditional block.  
It helps TypeScript refine union types into more specific types, giving you **better IntelliSense and type safety**.

---
- **Type Guards** are expressions that check and narrow types.
    
- Can be built-in (`typeof`, `instanceof`, `in`) or custom (via **type predicates**).
    
- Prevents unnecessary type assertions (`as`) and runtime errors.
    
- Makes union types much safer to work with.
    
---

### ✅ Example 1: Using `typeof`

```ts
function printId(id: string | number) {
  if (typeof id === "string") {
    console.log(id.toUpperCase()); // ✅ id is string here
  } else {
    console.log(id.toFixed(2));    // ✅ id is number here
  }
}
```

---

### ✅ Example 2: Using `instanceof`

```ts
class Dog { bark() { console.log("Woof!"); } }
class Cat { meow() { console.log("Meow!"); } }

function makeSound(animal: Dog | Cat) {
  if (animal instanceof Dog) {
    animal.bark();  // ✅ Safe
  } else {
    animal.meow();  // ✅ Safe
  }
}
```

---

### ✅ Example 3: Using **Type Predicates** (Custom Type Guards)

```ts
type Student = { id: number; name: string };
type Teacher = { id: number; subject: string };

function isTeacher(person: Student | Teacher): person is Teacher {
  return (person as Teacher).subject !== undefined;
}

function printPerson(person: Student | Teacher) {
  if (isTeacher(person)) {
    console.log("Teacher of:", person.subject); // ✅ Teacher
  } else {
    console.log("Student:", person.name);       // ✅ Student
  }
}
```

---

### 🔑 Key Points (for interview)

- **Type Guards** are expressions that check and narrow types.
    
- Can be built-in (`typeof`, `instanceof`, `in`) or custom (via **type predicates**).
    
- Prevents unnecessary type assertions (`as`) and runtime errors.
    
- Makes union types much safer to work with.
    

---

⚡ **Crisp one-liner:**

> A Type Guard is a runtime check (like `typeof`, `instanceof`, or a custom function with a type predicate) that tells TypeScript how to narrow a variable to a more specific type.

---

👉 Do you want me to also compare **Type Guards vs Type Casting (`as`)** — since that’s another thing interviewers love to ask?
# 🚀 `in` operator narrowing


## **1. What is `in` operator narrowing?**

The **`in` operator** in JavaScript checks whether a given property exists in an object.

In **TypeScript**, if you use it on a variable that could be multiple types, TS **narrows** the type depending on whether that property exists.

---

## **2. Basic syntax**

```ts
"propertyName" in object
```

- `"propertyName"` must be a string literal (or string variable) representing the key you’re checking.
    
- `object` is the variable you’re checking against.
    

---

## **3. Example**

```ts
type Fish = { swim: () => void };
type Bird = { fly: () => void };

function move(animal: Fish | Bird) {
    if ("swim" in animal) {
        // ✅ animal is narrowed to Fish here
        animal.swim();
    } else {
        // ✅ animal is narrowed to Bird here
        animal.fly();
    }
}
```

### How TS thinks:

- At first, `animal` is `Fish | Bird`.
    
- Inside `if ("swim" in animal)`, only a `Fish` type could have `"swim"`, so TS narrows it to `Fish`.
    
- In the `else` block, TS knows it must be `Bird`.
    

---

## **4. Why it’s useful**

- You can narrow **object union types** by checking which **properties** exist.
    
- This works **even if two types have no shared fields**.
    

---

## **5. Practical real-world example**

```ts
type Admin = { role: "admin"; permissions: string[] };
type User = { role: "user"; email: string };

function getUserInfo(person: Admin | User) {
    if ("permissions" in person) {
        console.log(`Admin with perms: ${person.permissions.join(", ")}`);
    } else {
        console.log(`User with email: ${person.email}`);
    }
}
```

Here, the `in` operator lets us safely access **only** the properties that belong to that specific type.

---

## **6. Extra tip**

You can also use `in` narrowing with **classes** and **interfaces**, not just plain objects:

```ts
interface Car { drive(): void }
interface Boat { sail(): void }

function useVehicle(v: Car | Boat) {
    if ("drive" in v) {
        v.drive();
    } else {
        v.sail();
    }
}
```

---

# 🚀 `instanceof` and Type `predicates`

## **1. `instanceof` Narrowing**

### **What it does**

- Checks if an object is an **instance** of a specific class (or constructor function).
    
- If `true`, TypeScript **narrows** the variable to that class type in that branch.
    

### **Syntax**

```ts
object instanceof ClassName
```

---

### **Example**

```ts
class Dog {
    bark() { console.log("Woof!"); }
}

class Cat {
    meow() { console.log("Meow!"); }
}

function makeNoise(animal: Dog | Cat) {
    if (animal instanceof Dog) {
        // ✅ animal is Dog here
        animal.bark();
    } else {
        // ✅ animal is Cat here
        animal.meow();
    }
}

const myDog = new Dog();
const myCat = new Cat();

makeNoise(myDog); // 🐶 Woof!
makeNoise(myCat); // 🐱 Meow!

```

💡 **Important**:

- `instanceof` only works for **classes** (and constructor functions), not for plain object types.
    
- It works at **runtime** because it uses the JS prototype chain to check.
    

---
📌 **Why this works**:  
`instanceof` checks if `animal` was created using `new Dog()` or `new Cat()` by looking at the **prototype chain** in JavaScript.

---

### Where you'd use `instanceof`

- You have **real classes** in your code.
    
- You want to **differentiate between different class instances**.
    

Example:
```ts

if (error instanceof SyntaxError) {   

	console.log("This is a syntax error");
	 
 }
	
```

## **2. Type Predicates**

### **What they are**

A **type predicate** is a custom function that tells TypeScript:

> “If I return true, you can treat this value as a more specific type.”

It’s how we create **custom type narrowing logic**.

---

### **Syntax**

```ts
function isTypeName(arg: unknown): arg is TypeName {
    // some check
    return trueOrFalse;
}
```

- `arg is TypeName` is the **predicate** part — tells TS the narrowed type if true.
    

Here, `arg is TypeName` is the **type predicate**.  
It tells TypeScript: “If this function returns `true`, then `arg` is of type `TypeName`.”

---

### **Example**

```ts
type Fish = { swim: () => void };
type Bird = { fly: () => void };

// Custom type check function
function isFish(animal: Fish | Bird): animal is Fish {
    // Checks if the object has a 'swim' function
    return typeof (animal as Fish).swim === "function";
}

function move(animal: Fish | Bird) {
    if (isFish(animal)) {
        // ✅ Narrowed to Fish
        animal.swim();
    } else {
        // ✅ Narrowed to Bird
        animal.fly();
    }
}

const goldfish: Fish = { swim: () => console.log("🐟 swimming") };
const parrot: Bird = { fly: () => console.log("🦜 flying") };

move(goldfish); // 🐟 swimming
move(parrot);   // 🦜 flying

```


📌 **Why this works**:  
 Unlike `instanceof`, we don’t need the type to come from a class — just a **check** that tells TypeScript “If this returns `true`, you can trust me that it’s a Fish.”

---

## **3. `instanceof` vs Type Predicate**

|Feature|`instanceof`|Type Predicate|
|---|---|---|
|Works for|Classes & constructor functions|Any type (even plain objects, unions)|
|Runtime check?|Yes, via prototype chain|Yes, based on your custom logic|
|Compile-time narrowing|✅|✅|
|Use case|You have classes|You have interfaces, object types, or unions without classes|

---

## **4. Real-world example combining both**

```ts
class Car { drive() { console.log("Driving"); } }
interface Bicycle { pedal(): void }

function isBicycle(vehicle: any): vehicle is Bicycle {
    return typeof vehicle.pedal === "function";
}

function useVehicle(vehicle: Car | Bicycle) {
    if (vehicle instanceof Car) {
        vehicle.drive();
    } else if (isBicycle(vehicle)) {
        vehicle.pedal();
    }
}
```

Here:

- `instanceof` is used for the class check.
    
- `isBicycle` type predicate is used for an interface check.
    

---

# 🚀Discriminated unions


## **1. The idea**

A **discriminated union** is a **union type** where **each variant has a special “tag” property** that tells you which one it is.  
That “tag” lets TypeScript automatically **narrow** the type inside conditionals — no custom functions needed.

📌 You’ll sometimes hear them called **tagged unions** or **algebraic data types**.

---

## **2. Structure**

To make a discriminated union in TypeScript, you need:

1. **A union type** (multiple possible shapes of an object).
    
2. **A common property** (the “discriminator”) that exists in _all_ members, but has a **different literal value** in each.
    

---

## **3. Example**

```ts
interface Circle {
    kind: "circle"; // literal type — the discriminator
    radius: number;
}

interface Square {
    kind: "square";
    sideLength: number;
}

interface Rectangle {
    kind: "rectangle";
    width: number;
    height: number;
}

// Discriminated union type
type Shape = Circle | Square | Rectangle;

// Using it
function getArea(shape: Shape): number {
    // TS automatically narrows based on `kind`
    if (shape.kind === "circle") {
        return Math.PI * shape.radius ** 2;
    } else if (shape.kind === "square") {
        return shape.sideLength ** 2;
    } else {
        return shape.width * shape.height;
    }
}

console.log(getArea({ kind: "circle", radius: 5 })); // 78.53...
console.log(getArea({ kind: "square", sideLength: 4 })); // 16
```

---

## **4. Why it works**

- The `kind` property acts like a label telling TS **exactly which type you have**.
    
- TypeScript can **narrow the union** just by checking the discriminator.
    

---

## **5. Real-world uses**

- **API responses** that can return different shapes:
    

```ts
interface Success {
    status: "success";
    data: string;
}

interface Error {
    status: "error";
    message: string;
}

type ApiResponse = Success | Error;

function handleResponse(res: ApiResponse) {
    if (res.status === "success") {
        console.log("Data:", res.data);
    } else {
        console.error("Error:", res.message);
    }
}
```

- **State management** in React or Redux
    
- **Event handling** (different event types with unique payloads)
    
- **Form validation** (different rules depending on field type)
    

---

## **6. Benefits**

- **Type safety** without extra runtime checks.
    
- **Autocomplete** works perfectly once TypeScript narrows the type.
    
- No need for `instanceof` or custom type predicates in most cases.
    

---

# 🚀 `never` type and `Exhaustiveness` Checking


## what is `never`?

> `never` is the type for values that **can’t exist**.  
> If a variable has type `never`, it means “there is no possible value here.”

Think of it as the **bottom** of the type system:

- `never` is assignable to **every** type.
    
- **No** type (except `never` itself) is assignable **to** `never`.
    

### where `never` shows up

1. **Functions that never return**
    

```ts
function fail(message: string): never {
  throw new Error(message);    // always throws ⇒ never returns
}

function loopForever(): never {
  while (true) {}
}
```

2. **Fully narrowed impossibilities**
    

```ts
type A = "x" | "y";
function f(a: A) {
  if (a === "x") { /* ... */ }
  else if (a === "y") { /* ... */ }
  else {
    // Here, a is impossible
    const unreachable: never = a; // ⛔ compile error if union ever grows
  }
}
```

3. **Empty array literal before inference**
    

```ts
const xs = [];     // xs: never[] initially (no info yet)
xs.push(1);        // now widens to number[]
```

(usually you’ll annotate to avoid this surprise: `const xs: number[] = [];`)

### `never` vs similar types (quick compare)

|Type|Means at compile time|Can you use it at runtime?|Typical use|
|---|---|---|---|
|`never`|impossible value|no return/unreachable|exhaustiveness checks, throw/loop|
|`void`|function returns no value|function _returns_ (undefined)|APIs that “don’t return anything”|
|`unknown`|some value, type unknown|must narrow before using|safe alternative to `any`|
|`any`|opt-out of checking|anything goes|avoid if possible|

---

## exhaustiveness checking (the real power move)

> “Exhaustiveness checking” is making the compiler prove that you handled **every possible variant** of a union.  
> If a new variant gets added later, TypeScript will **fail the build** until you handle it.

## pattern 1: `switch` + `assertNever`

Create a little helper:

```ts
function assertNever(x: never): never {
  throw new Error(`Unexpected object: ${JSON.stringify(x)}`);
}
```

Use it with a **discriminated union**:

```ts
type Circle    = { kind: "circle"; radius: number };
type Square    = { kind: "square"; side: number };
type Rectangle = { kind: "rectangle"; w: number; h: number };

type Shape = Circle | Square | Rectangle;

function area(s: Shape): number {
  switch (s.kind) {
    case "circle":
      return Math.PI * s.radius ** 2;
    case "square":
      return s.side ** 2;
    case "rectangle":
      return s.w * s.h;
    default:
      // If someone later adds { kind: "triangle", ... },
      // this line becomes a type error until you handle it.
      return assertNever(s);
  }
}
```

Why this works:

- Inside `default`, `s` should be **`never`** if all cases are handled.
    
- If `Shape` grows, `s` is no longer `never` → TypeScript errors here, forcing you to add the new case.
    

## pattern 2: `if/else` chains with a final `assertNever`

```ts
function area2(s: Shape): number {
  if (s.kind === "circle") return Math.PI * s.radius ** 2;
  if (s.kind === "square") return s.side ** 2;
  if (s.kind === "rectangle") return s.w * s.h;

  // Exhaustive guard:
  return assertNever(s);
}
```

## pattern 3: explicit `never` variable

Useful when you can’t call a function in the last branch:

```ts
function handle(shape: Shape) {
  // ...cases...
  const _exhaustiveCheck: never = shape; // ⛔ error if any case missing
}
```

---

## more real-world examples

## reducers / action handling

```ts
type Action =
  | { type: "increment"; by: number }
  | { type: "reset" }
  | { type: "set"; value: number };

function reducer(state: number, action: Action): number {
  switch (action.type) {
    case "increment":
      return state + action.by;
    case "reset":
      return 0;
    case "set":
      return action.value;
    default:
      return assertNever(action);
  }
}
```

Add `{ type: "decrement" }` later? The compiler points **exactly** where you forgot to handle it.

## API responses

```ts
type ApiResponse =
  | { status: "ok"; data: string }
  | { status: "error"; message: string };

function handle(res: ApiResponse) {
  switch (res.status) {
    case "ok":    return res.data;
    case "error": throw new Error(res.message);
    default:      return assertNever(res);
  }
}
```

---

## subtle tips & gotchas

- **Don’t return from `default`** with a value of a wide type; always call an `assertNever` (or assign to a `never` variable). That’s what enforces exhaustiveness.
    
- Use **discriminated unions** (a literal tag like `kind`/`type`) to make narrowing clean and automatic.
    
- Enable helpful flags in `tsconfig.json`:
    
    - `"strict": true`
        
    - `"noImplicitReturns": true` (helps catch missing branches)
        
    - `"noFallthroughCasesInSwitch": true`
        
- Avoid silencing errors with casts like `as never` — that defeats the purpose.
    

---

## quick mental model

- `never` = “this can’t happen.”
    
- Exhaustiveness check = “prove to the compiler that nothing unhandled can happen.”
    
- `assertNever` is the bridge that turns a **missed case** into a **compile-time error**.
    

If you want, I can refactor one of your existing union types (from your earlier examples) to use `assertNever` so you can see how a tiny helper can guard an entire codebase from missed cases.