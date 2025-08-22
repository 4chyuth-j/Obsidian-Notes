# 🚀Public, Private and Protected 

## 1️⃣ The core idea

A **class** groups data (**fields**) and behavior (**methods**) together.  
But sometimes you don’t want every variable or method to be accessible everywhere — that’s where **access modifiers** come in.

Think of it like **a house**:

- `public` = the living room — **anyone** can walk in.
    
- `private` = your bedroom — only **you** can enter.
    
- `protected` = your family room — only you **and your children** (subclasses) can enter.
    

---

## 2️⃣ `public` (default)

**Meaning:**

- Can be accessed from anywhere:
    
    - inside the class
        
    - outside the class
        
    - in subclasses
        

**Syntax:**

```ts
class Car {
  public brand: string; // 'public' is optional (default)

  constructor(brand: string) {
    this.brand = brand;
  }

  public drive() { // accessible anywhere
    console.log(`${this.brand} is moving 🚗`);
  }
}

const c = new Car("Tesla");
console.log(c.brand); // ✅ works
c.drive(); // ✅ works
```

If you don’t write any modifier, TypeScript assumes `public`.

---

## 3️⃣ `private`

**Meaning:**

- Can be accessed **only inside the same class**.
    
- Not visible in:
    
    - subclasses
        
    - outside code
        

**Syntax:**

```ts
class BankAccount {
  private balance: number = 0; // only inside this class

  deposit(amount: number) {
    this.balance += amount; // ✅ works here
  }

  getBalance() {
    return this.balance; // ✅ works here
  }
}

const acc = new BankAccount();
acc.deposit(100);
// console.log(acc.balance); ❌ ERROR — can't access directly
```

⚠ **Note:**  
TypeScript `private` is **compile-time only**.  
At runtime (in JS), the property still exists, but TypeScript won’t let you touch it.  
If you want **real privacy** at runtime, you can use `#private` fields:

```ts
class Example {
  #secret = 42;
}
```

---

## 4️⃣ `protected`

**Meaning:**

- Works like `private`, **but** subclasses can also access it.
    
- Still **not** accessible from outside the class or subclass.
    

**Syntax:**

```ts
class Person {
  protected name: string;
  constructor(name: string) {
    this.name = name;
  }
}

class Student extends Person {
  introduce() {
    console.log(`Hi, I am ${this.name}`); // ✅ subclass can access
  }
}

const s = new Student("Achyuth");
s.introduce();
// console.log(s.name); ❌ ERROR — outside access not allowed
```

---

## 5️⃣ Side-by-side example

```ts
class Parent {
  public pub = "public data";
  private pri = "private data";
  protected pro = "protected data";

  showAll() {
    console.log(this.pub); // ✅
    console.log(this.pri); // ✅
    console.log(this.pro); // ✅
  }
}

class Child extends Parent {
  showInherited() {
    console.log(this.pub); // ✅
    // console.log(this.pri); ❌ can't access private
    console.log(this.pro); // ✅ can access protected
  }
}

const p = new Parent();
console.log(p.pub); // ✅
p.showAll(); // ✅
// console.log(p.pri); ❌
// console.log(p.pro); ❌

const c = new Child();
c.showInherited(); // ✅
```

---

## 6️⃣ When to use which?

|Modifier|Who can access?|Use case|
|---|---|---|
|**public**|Everyone|Public API of your class — things you want users to call.|
|**private**|Only same class|Hide sensitive data or internal helper methods.|
|**protected**|Class + subclasses|Keep something hidden from outside, but let child classes use it.|

---

💡 **Quick mental model:**

- `public` → **Door wide open** 🚪
    
- `private` → **Locked safe** 🔒
    
- `protected` → **Family-only access** 🏠
    

---



# 🚀Class example (beginner level)

Alright, Achyuth — let’s dissect your code line-by-line,  
then I’ll rewrite it in a **production-level** style so it’s clean, safe, and scalable.

---

## 1️⃣ Your code, explained

```ts
class Users {
    email: string;           // public by default, can be accessed anywhere
    name: string;            // public by default
    private city: string = 'Kollam'; // private, only accessible INSIDE this class

    constructor(email: string, name: string) {
        this.email = email;   // assigning constructor parameters to fields
        this.name = name;
    }

    getCity(): string {      // public method
        return this.city;    // allowed because it's inside the same class
    }
}
```

### Key points here:

- **`email`** and **`name`**:  
    Public by default → you can do `achyuth.email` or `achyuth.name` from anywhere.
    
- **`private city`**:  
    Cannot be accessed from outside the class. Only `getCity()` inside the class can use it.
    
- **`constructor(...)`**:  
    Runs automatically when you create a new instance with `new Users(...)`.  
    It sets the `email` and `name`.
    
- **`getCity()`**:  
    A **public method** that acts as a **getter** — a safe way to read private data.
    

---

## 2️⃣ Why `achyuth.city` doesn’t work

```ts
const achyuth = new Users('ach@gmail.com','achu');
achyuth.city; // ❌ Error — city is private
```

Since `city` is marked `private`, it’s only accessible **inside** the `Users` class.  
If you need it, you must call:

```ts
achyuth.getCity(); // ✅ returns "Kollam"
```

---

## 3️⃣ How it works in memory (simplified)

When you run:

```ts
const achyuth = new Users('ach@gmail.com', 'achu');
```

- TS checks types at compile time.
    
- At runtime, in JavaScript, it creates an object like:
    

```js
{
  email: "ach@gmail.com",
  name: "achu",
  city: "Kollam" // still exists, but TS stops you from touching it directly
}
```

So **`private` is not true runtime privacy** — it’s a **compile-time rule**.  
If you want _real_ privacy, you’d use `#city` instead of `private city`.

---

## 4️⃣ Production-level rewrite

Here’s how I’d write this for a **real-world project**:

```ts
class User {
  // ✅ Use readonly for values that should never change after creation
  public readonly email: string;
  public name: string;

  // ✅ Use #private for runtime privacy (ECMAScript standard)
  #city: string = "Kollam";

  constructor(email: string, name: string) {
    if (!this.isValidEmail(email)) {
      throw new Error("Invalid email format");
    }
    this.email = email;
    this.name = name;
  }

  // Public getter for private field
  public getCity(): string {
    return this.#city;
  }

  // Public setter for city with validation
  public setCity(newCity: string): void {
    if (newCity.trim().length < 3) {
      throw new Error("City name too short");
    }
    this.#city = newCity;
  }

  // ✅ Keep helper methods private
  private isValidEmail(email: string): boolean {
    return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
  }
}

// Usage
const achyuth = new User("ach@gmail.com", "Achu");
console.log(achyuth.email); // ✅
console.log(achyuth.getCity()); // ✅
achyuth.setCity("Trivandrum"); // ✅ updates city
```

---

## 5️⃣ Why this version is **production-ready**

1. **Validation** — checks email format before saving.
    
2. **`readonly`** — ensures `email` can’t be changed later.
    
3. **`#private`** — true runtime privacy.
    
4. **Getter & Setter** — controlled access to private data.
    
5. **Private helper methods** — internal logic hidden from the outside.
    

---

# 🚀Getters and Setters

**getters** and **setters** are like **controlled doors** into your class’s private room.  
They decide **how you read and change** a property, instead of just letting anyone poke it directly.

---

## 1️⃣ The problem they solve

Without getters/setters:

```ts
class User {
  public name: string;
  constructor(name: string) {
    this.name = name;
  }
}

const u = new User("Achu");
u.name = ""; // ❌ name becomes empty — no control
```

If we want to **protect** data, add **validation**, or even **compute a value**, we need a middleman.

That’s where **getters** and **setters** come in.

---

## 2️⃣ What is a getter?

- A method that **looks like a property** when you read it.
    
- Runs code when you **access** the value.
    

Example:

```ts
class User {
  private _name: string;

  constructor(name: string) {
    this._name = name;
  }

  // GETTER
  get name(): string {
    return this._name.toUpperCase(); // computed value
  }
}

const u = new User("Achu");
console.log(u.name); // "ACHU" ✅ looks like a property, but it's a method
```

---

## 3️⃣ What is a setter?

- A method that **looks like a property** when you assign to it.
    
- Runs code when you **change** the value.
    

Example:

```ts
class User {
  private _name: string;

  constructor(name: string) {
    this._name = name;
  }

  // GETTER
  get name(): string {
    return this._name;
  }

  // SETTER
  set name(value: string) {
    if (value.trim() === "") {
      throw new Error("Name cannot be empty");
    }
    this._name = value;
  }
}

const u = new User("Achu");
u.name = "Achyuth"; // ✅ calls setter, updates safely
console.log(u.name); // ✅ calls getter, prints "Achyuth"

// u.name = ""; // ❌ Error: Name cannot be empty
```

---

## 4️⃣ Key things about getters/setters

- **Look like properties** but work like functions.
    
- Can add **validation**, **transform data**, or even **prevent changes**.
    
- Usually, you use a **private field** (e.g., `_name`) to store actual data and getters/setters to control access.
    
- In TypeScript, getters **must** return a value, and setters **must** take exactly **one parameter**.
    

---

## 5️⃣ Real-life analogy

- **Getter** = Reading info from a receptionist instead of going into the office yourself.
    
- **Setter** = Giving the receptionist your updated info — they’ll check if it’s valid before saving it.
    

---

## 6️⃣ Quick example with both:

```ts
class BankAccount {
  private _balance = 0;

  get balance(): number {
    console.log("Getting balance...");
    return this._balance;
  }

  set balance(amount: number) {
    if (amount < 0) throw new Error("Cannot set negative balance");
    console.log("Updating balance...");
    this._balance = amount;
  }
}

const acc = new BankAccount();
acc.balance = 500;  // calls setter
console.log(acc.balance); // calls getter
```

---

# 🚀Application of Getters and Setters

## **1️⃣ Why use getters and setters?**

The main reasons are:

### **a) Data Protection (Encapsulation)**

- You keep your **actual data** private (`private` or `#private`), and control how people access or modify it.
    
- Prevents invalid, harmful, or unexpected changes.
    

Example:

```ts
class BankAccount {
  #balance = 0;

  get balance() {
    return this.#balance;
  }

  set balance(amount: number) {
    if (amount < 0) throw new Error("Balance cannot be negative");
    this.#balance = amount;
  }
}
```

Here, nobody can directly make your balance negative.

---

### **b) Validation before setting**

- You can **check** new values before storing them.
    
- Prevents bad data from entering your system.
    

Example:

```ts
set email(value: string) {
  if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(value)) {
    throw new Error("Invalid email format");
  }
  this.#email = value;
}
```

---

### **c) Computed properties**

- Sometimes a value is **derived** from other data instead of being stored directly.
    
- A getter can calculate it **on the fly**.
    

Example:

```ts
get fullName() {
  return `${this.firstName} ${this.lastName}`;
}
```

---

### **d) Read-only properties**

- You can give a getter without a setter → the value is **read-only** from outside.
    

```ts
get createdAt() {
  return this.#createdAt;
}
```

---

### **e) Logging, Security, and Triggers**

- You can run extra code when something is read or changed (logging, analytics, side-effects).
    

```ts
set password(newPass: string) {
  console.log(`Password updated at ${new Date()}`);
  this.#password = hash(newPass);
}
```

---

## **2️⃣ Where you’ll actually use this in real projects**

### **a) In Models / Entities**

If you’re making a **User**, **Order**, **Product**, **Account** class:

- Hide sensitive fields (password, tokens, internal IDs).
    
- Validate inputs before saving.
    
- Format outputs for UI.
    

---

### **b) In API Wrappers**

When wrapping data from an API:

- Ensure values match expected formats.
    
- Auto-convert data (e.g., string date → Date object).
    

```ts
get createdAt(): Date {
  return new Date(this.#rawDate);
}
```

---

### **c) In UI Frameworks**

In frameworks like Angular, Vue, React (with TS):

- Getters can be used to return **computed values** based on state.
    
- Setters can **trigger updates** or validations before UI changes.
    

---

### **d) In Libraries & SDKs**

If you write a library:

- You don’t expose internal structure directly.
    
- You allow users to interact **only through safe, controlled access**.
    

---

### **e) For Backward Compatibility**

If your class’s internal structure changes later:

- Keep getter/setter names the same, so existing code still works.
    
- Inside, change how you store or calculate values without breaking API.
    

---

## **3️⃣ TL;DR mental model**

Think of **getters** and **setters** as:

- **A guard at the door**: Checks ID before letting someone in.
    
- **A filter for outgoing info**: Controls what details you actually give out.
    

---


# 🚀`Implements` vs `Extends` keywords

## 🟢 `extends`

- Used with **classes** and **interfaces**.
    
- Means **inheritance** → one thing is a specialized version of another.
    
- Child **inherits properties/methods** from parent.
    

### Example 1: Class extends Class

```ts
class Person {
  name: string;
  constructor(name: string) {
    this.name = name;
  }
  greet() {
    console.log(`Hello, I'm ${this.name}`);
  }
}

class Student extends Person {
  rollNo: number;
  constructor(name: string, rollNo: number) {
    super(name); // ✅ must call parent constructor
    this.rollNo = rollNo;
  }
}

const s = new Student("Achyuth", 101);
s.greet(); // ✅ inherited method
```

👉 `Student` **is-a** `Person` (specialized version).

---

### Example 2: Interface extends Interface

```ts
interface Animal {
  name: string;
}
interface Dog extends Animal {
  breed: string;
}

const d: Dog = { name: "Tommy", breed: "Labrador" };
```

👉 `Dog` **is-an** `Animal` with extra features.

---

## 🔵 `implements`

- Used with **classes**.
    
- Means the class **agrees to follow a contract** defined by an interface.
    
- The class **must implement all properties and methods** declared in the interface.
    

### Example:

```ts
interface Shape {
  area(): number;
}

class Circle implements Shape {
  radius: number;
  constructor(radius: number) {
    this.radius = radius;
  }
  area(): number {
    return Math.PI * this.radius * this.radius;
  }
}
```

👉 `Circle` is **not extending** `Shape` (no inheritance). Instead, it’s **promising**:  
"I will provide an `area()` method as defined in `Shape`."

---

## ⚡ `extends` vs `implements` (Key Difference)

|Feature|`extends` 🟢|`implements` 🔵|
|---|---|---|
|Used with|Classes + Interfaces|Only Classes|
|Meaning|Inherit from parent|Enforce contract|
|Inherits implementation?|✅ Yes (methods/properties come along)|❌ No (class must write methods)|
|Multiple allowed?|❌ Only single class inheritance|✅ A class can implement many interfaces|
|Use case|Reuse behavior|Ensure structure|

---

## 🟣 Combined Example

```ts
interface CanFly {
  fly(): void;
}
interface CanSwim {
  swim(): void;
}

class Animal {
  eat() {
    console.log("Eating...");
  }
}

// A Duck is an Animal (extends) AND must follow CanFly & CanSwim contracts (implements)
class Duck extends Animal implements CanFly, CanSwim {
  fly() { console.log("Flying..."); }
  swim() { console.log("Swimming..."); }
}

const d = new Duck();
d.eat(); // inherited from Animal
d.fly(); // from CanFly interface
d.swim(); // from CanSwim interface
```

👉 `Duck`:

- **extends** `Animal` → inherits behavior
    
- **implements** `CanFly` + `CanSwim` → forced to write its own methods
    

---

## ✅ Summary

- **`extends`** → reuse code via **inheritance** (child gets parent’s behavior).
    
- **`implements`** → enforce **structure** via contract (class must define methods).
    
- A class can **extend one parent class** but **implement multiple interfaces**.
    

---

Do you want me to also explain how **interfaces vs abstract classes** fit into this (since both are often compared with `implements`)?

# 🚀what is an abstract class?

https://www.geeksforgeeks.org/typescript/typescript-abstract-class/

An **abstract class** is a base class that **can’t be instantiated** directly.  
It lets you:

- **share common code** (methods/fields) for a family of subclasses, and
    
- **force** those subclasses to implement certain methods/properties (marked `abstract`).
    

Think of it like a **template**: it gives structure + some default behavior, but leaves key pieces to be filled in by the child classes.

---

## quick rules (cheat sheet)

- `abstract class X { ... }` — cannot do `new X()`.
    
- Inside it, you can declare:
    
    - **abstract methods/properties** (no body) → must be implemented by subclasses.
        
    - **concrete methods/properties** (with code) → shared behavior.
        
- Subclasses use `extends` and **must** implement all `abstract` members.
    
- Use `override` when implementing inherited methods (helps compiler catch mistakes).
    
- Visibility works normally: `public`, `protected`, `private`.
    
- Abstract **static** members aren’t supported; keep abstract members instance-level.
    
- At runtime, “abstract” disappears (it’s a TS compile-time thing), but the base class still exists for `instanceof` checks.
    

---

## a minimal example

```ts
abstract class Shape {
  // abstract = no implementation here
  abstract area(): number;

  // shared implementation
  move(dx: number, dy: number) {
    console.log(`moving by (${dx}, ${dy})`);
  }
}

class Circle extends Shape {
  constructor(private r: number) { super(); }

  override area(): number {
    return Math.PI * this.r * this.r;
  }
}

// const s = new Shape();   // ❌ Error: cannot create an instance of an abstract class
const c = new Circle(10);   // ✅
console.log(c.area());      // 314.159...
c.move(5, 3);               // shared behavior
```

---

## abstract **properties** too

You can require subclasses to supply a property:

```ts
abstract class Model {
  abstract table: string; // must be provided by child

  save() {
    console.log(`Saving to ${this.table}...`);
  }
}

class UserModel extends Model {
  table = "users";  // ✅ fulfills abstract requirement
}

new UserModel().save(); // "Saving to users..."
```

---

## a powerful pattern: **Template Method**

The base class defines the **algorithm steps**; subclasses fill in the variable parts.

```ts
type Receipt = { id: string; amount: number };

abstract class Payment {
  // final-ish workflow (don’t override this; keep steps protected/abstract)
  pay(amount: number): Receipt {
    this.validate(amount);
    const receipt = this.charge(amount);
    this.audit(receipt);
    return receipt;
  }

  protected abstract validate(amount: number): void;
  protected abstract charge(amount: number): Receipt;

  protected audit(r: Receipt) {
    // shared auditing
    console.log(`audited tx ${r.id}`);
  }
}

class UpiPayment extends Payment {
  protected override validate(amount: number) {
    if (amount <= 0) throw new Error("Invalid amount");
  }
  protected override charge(amount: number): Receipt {
    return { id: crypto.randomUUID(), amount };
  }
}

const p = new UpiPayment();
p.pay(500);
```

Why this rocks:

- All payments follow the **same flow** (`pay`), ensuring consistency.
    
- Each gateway implements only what differs (`validate`, `charge`).
    

---

## real-world use cases you’ll actually meet

1. **Domain models with shared behavior**  
    Example: `Account` base with balance math; subclasses `SavingsAccount`, `CheckingAccount` implement `monthlyUpdate()`.
    
    ```ts
    abstract class Account {
      protected balance = 0;
      constructor(public readonly id: string) {}
      deposit(a: number) { if (a<=0) throw; this.balance += a; }
      getBalance() { return this.balance; }
      abstract monthlyUpdate(): void;
    }
    
    class Savings extends Account {
      constructor(id: string, private rate = 0.03) { super(id); }
      override monthlyUpdate() { this.balance += this.balance * this.rate; }
    }
    ```
    
2. **Data access (Repository pattern)**  
    Share caching/validation; let subclasses define constraints or storage specifics.
    
    ```ts
    interface Entity { id: string }
    
    abstract class Repo<T extends Entity> {
      protected store = new Map<string, T>();
    
      add(item: T) {
        this.validate(item);
        this.store.set(item.id, item);
      }
      get(id: string) { return this.store.get(id); }
    
      protected abstract validate(item: T): void; // each repo decides rules
    }
    
    type User = { id: string; email: string };
    
    class UserRepo extends Repo<User> {
      protected override validate(u: User) {
        if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(u.email)) throw new Error("Bad email");
      }
    }
    ```
    
3. **SDK/Client base classes**  
    Provide retry, logging, auth headers in base; subclasses implement the actual HTTP calls/endpoints.
    
4. **Plugin systems**  
    Base class defines the hooks; each plugin implements `init()`, `execute()`, `cleanup()`.
    
5. **UI/ViewModel hierarchies** (even in React-less or Angular projects)  
    Base handles state/validation; specific screens implement `submit()` or `load()`.
    

---

## abstract class vs interface (when to choose which)

|Use…|When you need…|
|---|---|
|**Interface**|A contract/shape only. No code. Multiple “implements” allowed. Great for DTOs, props, function types.|
|**Abstract class**|A contract **plus** shared implementation/state, lifecycle/flow control, protected helpers. Single inheritance (one base), but you can still `implement` interfaces too.|

Often you’ll combine them:

```ts
interface Auditable { audit(): string; }

abstract class BaseService implements Auditable {
  audit(): string { return "ok"; } // shared implementation
  abstract run(): Promise<void>;
}
```

---

## best practices

- Keep algorithm orchestration in the base (template method), keep variable parts abstract.
    
- Mark overrides with `override` and enable `noImplicitOverride` in tsconfig.
    
- Prefer `protected` over `private` when subclasses legitimately need access.
    
- Don’t expose half-baked/base-only classes — make them `abstract` so nobody instantiates them.
    
- Keep constructors light; validate inputs early.
    
- Avoid deep inheritance chains; if it’s getting deep, consider **composition** instead.
    

---

## common gotchas

- You **must** implement **all** abstract members in the subclass, with compatible types and **not weaker visibility** (can’t make a public abstract method protected in child).
    
- Always call `super(...)` **before** using `this` in subclass constructors.
    
- Remember: abstract is compile-time only; you can still do `value instanceof BaseClass` at runtime, but TS stops you from `new BaseClass()` during compile.
    

---

# 🚀`override` and `super` keyword
## 1. `override` keyword

**What it means**

- In TypeScript (with `--noImplicitOverride` enabled in `tsconfig.json`),  
    `override` tells the compiler:
    
    > “This method **already exists** in a parent class or abstract class, and I’m deliberately replacing it in this subclass.”
    

It’s not required by default, but enabling it catches typos & mistakes.

---

**Without `override`** (default behavior):

```ts
abstract class Animal {
  abstract makeSound(): void;
}

class Dog extends Animal {
  makeSound(): void {
    console.log("Bark");
  }
}
```

This works fine.

---

**With `override`** (recommended for safety):

```ts
abstract class Animal {
  abstract makeSound(): void;
}

class Dog extends Animal {
  override makeSound(): void {   // ✅ explicitly says: I’m overriding
    console.log("Bark");
  }
}
```

If you accidentally misspell:

```ts
class Dog extends Animal {
  override makeSond(): void {   // ❌ Error: no matching method to override
    console.log("Bark");
  }
}
```

This saves you from introducing a **new method** by accident instead of overriding the intended one.

---

**When to use:**

- Anytime you **replace or implement** a method from a base or abstract class.
    
- Makes refactoring safer: if the parent method changes name/signature, the compiler warns you.
    

---

## 2. `super` keyword

**What it means**

- Refers to the **parent class**.
    
- Used for:
    
    1. Calling the parent’s **constructor**.
        
    2. Calling a parent’s **method** that you’ve overridden.
        

---

### 2.1 In a constructor

If your subclass has its own constructor, you **must** call `super(...)` before using `this`.

```ts
class Animal {
  constructor(public name: string) {}
}

class Dog extends Animal {
  constructor(name: string, public breed: string) {
    super(name); // ✅ calls parent constructor
    console.log(`Created dog ${this.name}`);
  }
}
```

Why?

- The parent class might initialize important stuff.
    
- JavaScript won’t let you use `this` until after `super()` is called.
    

---

### 2.2 Calling parent methods

If you override a method but still want **some of the parent’s behavior**, use `super.methodName()`.

```ts
class Animal {
  speak() {
    console.log("Some generic animal sound");
  }
}

class Dog extends Animal {
  override speak() {
    super.speak(); // calls Animal.speak()
    console.log("Bark!");
  }
}

const d = new Dog();
d.speak();
// Output:
// Some generic animal sound
// Bark!
```

---

## In our **abstract class** example

```ts
abstract class Payment {
  pay(amount: number) {
    this.validate(amount);
    const receipt = this.charge(amount);
    this.audit(receipt);
    return receipt;
  }

  protected abstract validate(amount: number): void;
  protected abstract charge(amount: number): { id: string; amount: number };

  protected audit(r: { id: string; amount: number }) {
    console.log(`audited tx ${r.id}`);
  }
}

class UpiPayment extends Payment {
  protected override validate(amount: number) {
    if (amount <= 0) throw new Error("Invalid amount");
  }
  protected override charge(amount: number) {
    // I could call super.audit(...) here if needed
    return { id: crypto.randomUUID(), amount };
  }
}
```

- `override` ensures I’m correctly implementing the abstract methods.
    
- If `Payment` had a default `charge()` and I wanted to extend it,  
    I could call `super.charge(amount)` inside my `charge()` override.
    

---

✅ **Think of it like this:**

- `override` = "I’m replacing something that exists in my parent."
    
- `super` = "I want to access the parent’s version (constructor or method)."
    

---


# 🚀 `interface` vs. `abstract class`


They _look_ similar because both define **blueprints** for other classes, but they have **different purposes** and **rules**.

Let’s break it down like we’re building a mental model.

---

## **1️⃣ Core difference**

|Feature|**Interface**|**Abstract Class**|
|---|---|---|
|Purpose|_Shape contract_ — defines **what** a class should have.|_Blueprint with base logic_ — defines **what** and also provides **how** (default behavior).|
|Implementation in base|❌ No method body (only signatures).|✅ Can have both abstract methods (no body) **and** concrete methods (with body).|
|Fields / Properties|✅ Can define property names & types (but no values).|✅ Can define properties and also initialize them.|
|Multiple inheritance|✅ A class can `implements` multiple interfaces.|❌ A class can only `extends` one abstract class (single inheritance).|
|Constructors|❌ No constructors in interfaces.|✅ Can have constructors (for shared setup).|
|Access modifiers (`public`, `private`, `protected`)|❌ Not allowed — everything is public by design.|✅ Fully supported (public, private, protected).|
|Use case|When you only need a “shape” — no shared logic.|When you want **shared base logic + enforce certain implementations** in subclasses.|

---

## **2️⃣ Example: Interface**

```ts
interface PaymentProcessor {
  process(amount: number): void; // only says "must exist"
  currency: string; // just says there will be a currency string
}

class UpiPayment implements PaymentProcessor {
  currency = "INR"; // must implement
  process(amount: number): void {
    console.log(`Processing ₹${amount} via UPI`);
  }
}
```

- `PaymentProcessor` **cannot** have logic.
    
- It’s purely a **shape**:  
    "Any class claiming to be a `PaymentProcessor` must have a `process()` method and a `currency` property."
    

---

## **3️⃣ Example: Abstract Class**

```ts
abstract class Payment {
  protected currency = "INR"; // initialized value

  // Abstract method — must be implemented by subclass
  abstract process(amount: number): void;

  // Concrete method — already implemented
  receipt(amount: number) {
    console.log(`Receipt for ₹${amount} in ${this.currency}`);
  }
}

class UpiPayment extends Payment {
  process(amount: number): void {
    console.log(`Processing ₹${amount} via UPI`);
    this.receipt(amount); // reuses base class method
  }
}
```

- Here, `Payment` **both enforces** (`process()` must exist) and **provides default behavior** (`receipt()` method, currency default value).
    

---

## **4️⃣ When to use which?**

**Use an Interface when:**

- You just care about the _form/shape_ of a thing.
    
- You expect **multiple unrelated classes** to implement the same contract.
    
- You might use it in **type definitions** outside of classes (objects, functions, etc.).
    

**Use an Abstract Class when:**

- You want to share **common implementation logic** across subclasses.
    
- You want to enforce _and_ partially implement behavior.
    
- You need **access modifiers** to control visibility.
    
- You want to store state (`protected` or `private` variables).
    

---

## **5️⃣ Real-world analogy**

- **Interface** = Job description (lists skills required, but doesn’t tell you how to do them).
    
- **Abstract class** = Partially completed tool kit (some tools are ready, some you have to build yourself).
    

---

## **6️⃣ Hybrid approach**

TypeScript even lets **abstract classes implement interfaces**:

```ts
interface Loggable {
  log(): void;
}

abstract class Payment implements Loggable {
  abstract process(amount: number): void;

  log() {
    console.log("Logging payment...");
  }
}
```

This is **common in large projects** to combine flexibility (interfaces) with shared behavior (abstract class).

---

If you want, I can make you a **side-by-side diagram** showing exactly what you can and can’t do with an interface vs. abstract class — it makes remembering this super easy. Would you like me to do that?