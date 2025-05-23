
# 🚀Object methods
### **Defining Object Methods**

You can define methods in an object using **function expressions**, **ES6 shorthand**, or **arrow functions**.

#### **1. Using Function Expression**

```js
const person = {
  name: "Achyuth",
  greet: function () {
    return "Hello, " + this.name;
  }
};

console.log(person.greet()); // Output: Hello, Achyuth
```

#### **2. Using ES6 Method Shorthand**

```js
const person = {
  name: "Achyuth",
  greet() {
    return `Hello, ${this.name}`;
  }
};

console.log(person.greet()); // Output: Hello, Achyuth
```

#### **3. Using Arrow Functions (Not Recommended for Methods)**

Arrow functions **don't bind** `this` to the object.

```js
const person = {
  name: "Achyuth",
  greet: () => `Hello, ${this.name}` // `this` refers to global scope, not `person`
};

console.log(person.greet()); // Output: Hello, undefined
```

This happens because arrow functions **do not have their own `this`**.

---

### **Common Built-in Object Methods**

#### **1. Object.keys()** – Returns an array of object’s keys

```js
const obj = { a: 1, b: 2, c: 3 };
console.log(Object.keys(obj)); // Output: ['a', 'b', 'c']
```

#### **2. Object.values()** – Returns an array of object’s values

```js
console.log(Object.values(obj)); // Output: [1, 2, 3]
```

#### **3. Object.entries()** – Returns an array of key-value pairs

```js
console.log(Object.entries(obj)); // Output: [['a', 1], ['b', 2], ['c', 3]]
```

#### **4. Object.assign()** – Copies properties from one or more objects to a target object

```js
const target = { a: 1 };
const source = { b: 2, c: 3 };
Object.assign(target, source);
console.log(target); // Output: { a: 1, b: 2, c: 3 }
```

#### **5. Object.freeze()** – Prevents modification of an object

```js
const obj1 = { a: 1 };
Object.freeze(obj1);
obj1.a = 100; // No effect
console.log(obj1.a); // Output: 1
```

#### **6. Object.seal()** – Allows modification of properties but prevents adding or deleting properties

```js
const obj2 = { a: 1 };
Object.seal(obj2);
obj2.a = 100; // Works
obj2.b = 200; // No effect
console.log(obj2); // Output: { a: 100 }
```

#### **7. Object.hasOwnProperty()** – Checks if a property exists in an object

```js
console.log(obj.hasOwnProperty("a")); // Output: true
console.log(obj.hasOwnProperty("z")); // Output: false
```

---

### **Custom Object Methods Example**

```js
const calculator = {
  num1: 10,
  num2: 5,
  add() {
    return this.num1 + this.num2;
  },
  subtract() {
    return this.num1 - this.num2;
  }
};

console.log(calculator.add());      // Output: 15
console.log(calculator.subtract()); // Output: 5
```

# 🚀Type Casting in JavaScript

Type casting (also known as **type conversion**) is the process of converting a value from one data type to another. In JavaScript, this can happen **implicitly (coercion)** or **explicitly (manual conversion).**

---

## **1. Implicit Type Casting (Type Coercion)**

JavaScript automatically converts values when needed.

### **Example 1: String + Number → String**

```js
console.log("5" + 3);  // "53" (Number converted to String)
console.log("5" + true); // "5true" (Boolean converted to String)
```

### **Example 2: String - Number → Number**

```js
console.log("5" - 3);  // 2 (String converted to Number)
console.log("10" * 2); // 20 (String converted to Number)
console.log("5" - true); // 4 (true is 1, so "5" - 1 = 4)
```

### **Example 3: Boolean to Number**

```js
console.log(true + 1);  // 2 (true is 1)
console.log(false + 1); // 1 (false is 0)
```

---

## **2. Explicit Type Casting (Manual Conversion)**

You can manually convert data types using JavaScript methods.

### **Convert to String**

- `String(value)` or `value.toString()`

```js
console.log(String(123));    // "123"
console.log((123).toString()); // "123"
console.log(String(true));   // "true"
console.log(String(null));   // "null"
```

### **Convert to Number**

- `Number(value)` or `parseInt(value)` / `parseFloat(value)`

```js
console.log(Number("123"));    // 123
console.log(Number("123abc")); // NaN (Not a Number)
console.log(parseInt("123abc")); // 123 (Extracts only numbers)
console.log(parseFloat("10.5px")); // 10.5
console.log(Number(true));    // 1
console.log(Number(false));   // 0
console.log(Number(null));    // 0
console.log(Number(undefined)); // NaN
```

### **Convert to Boolean**

- `Boolean(value)`

```js
console.log(Boolean(1));  // true
console.log(Boolean(0));  // false
console.log(Boolean("hello"));  // true
console.log(Boolean(""));  // false
console.log(Boolean(null));  // false
console.log(Boolean(undefined));  // false
```

---

## **3. Special Cases**

```js
console.log(5 + null);    // 5 (null is converted to 0)
console.log("5" + null);  // "5null" (null is converted to "null")
console.log("5" - null);  // 5 (null is converted to 0)
console.log(undefined + 1); // NaN (undefined can't be converted)
console.log("5" * "2"); // 10 (Both strings converted to numbers)
```



# 🚀JavaScript Event Loop 

The Event Loop is what makes JavaScript asynchronous and non-blocking, allowing it to handle multiple tasks efficiently despite being single-threaded.

---

## 🔹 How JavaScript Works Behind the Scenes?

JavaScript uses:

1. Call Stack (Executes synchronous code)
    
2. Web APIs (Handles async tasks like setTimeout, fetch, etc.)
    
3. Callback Queue (Stores callbacks from async tasks)
    
4. Microtask Queue (Stores promises & other high-priority tasks)
    
5. Event Loop (Manages execution order)
    

---

## 🔹 How the Event Loop Works?

1️⃣ Synchronous code runs first (placed in the Call Stack).  
2️⃣ Async tasks (like setTimeout or fetch) move to Web APIs.  
3️⃣ Once completed, their callbacks go to the Callback Queue.  
4️⃣ Promises & high-priority tasks go to the Microtask Queue.  
5️⃣ The Event Loop keeps checking the Call Stack:

- If the Call Stack is empty, it moves the next task from the Microtask Queue first.
    
- If no microtasks remain, it moves a task from the Callback Queue.
    

---

## 🔹 Example: How the Event Loop Works

```js
console.log("1️⃣ Start");  // Runs first (Synchronous)

setTimeout(() => {
    console.log("3️⃣ Timeout callback");  // Runs later (Async)
}, 0);

Promise.resolve().then(() => console.log("2️⃣ Promise resolved")); // Microtask (Higher Priority)

console.log("4️⃣ End"); // Runs second (Synchronous)
```

  

### 🔍 Output

1️⃣ Start

4️⃣ End

2️⃣ Promise resolved  ✅ (Microtasks run before Callback Queue)

3️⃣ Timeout callback

  

✔ Why? Even though setTimeout has 0ms, it waits in the Callback Queue until synchronous & microtasks are done.

---

## 📌 Key Takeaways

|   |   |
|---|---|
|Concept|Explanation|
|Call Stack|Executes synchronous code (line by line).|
|Web APIs|Handles async tasks (setTimeout, fetch, etc.).|
|Callback Queue|Stores async callbacks (runs after Microtasks).|
|Microtask Queue|Stores Promises (higher priority than Callback Queue).|
|Event Loop|Keeps checking the Call Stack and moves tasks from queues.|

---


# **🚀Arrow Functions in JavaScript (`=>`)**

An **arrow function** is a shorter way to write functions in JavaScript, introduced in **ES6**. It is especially useful for **concise function expressions** and **lexical `this` binding**.

---

## **🔹 Syntax of Arrow Functions**

### **✅ Basic Syntax**

```js
const functionName = (param1, param2) => expression;
```

- No need for `function` keyword.
- **`return` is implicit** for one-line expressions.

---

## **🔹 Examples of Arrow Functions**

### **✅ Example 1: Regular Function vs Arrow Function**

```js
// Regular Function
function add(a, b) {
    return a + b;
}

// Arrow Function
const addArrow = (a, b) => a + b;

console.log(add(2, 3));       // 5
console.log(addArrow(2, 3));  // 5
```

✔️ **Shorter & cleaner syntax** with an **implicit return**.

---

### **✅ Example 2: Arrow Function with One Parameter**

```js
const square = x => x * x;  // No need for parentheses with one parameter
console.log(square(5));      // 25
```

✔️ **Parentheses around a single parameter can be omitted**.

---

### **✅ Example 3: Arrow Function with No Parameters**

```js
const greet = () => "Hello, World!";
console.log(greet());  // "Hello, World!"
```

✔️ **If no parameters, use `()`**.

---

### **✅ Example 4: Arrow Function with Multiple Statements**

```js
const multiply = (a, b) => {
    console.log(`Multiplying ${a} and ${b}`);
    return a * b;
};
console.log(multiply(3, 4));  // 12
```

✔️ **For multiple lines, `{}` and `return` are required**.

---

## **🔹 Differences Between Arrow Functions & Regular Functions**

|Feature|Arrow Function (`=>`)|Regular Function (`function`)|
|---|---|---|
|**Syntax**|Shorter & cleaner|More verbose|
|**`this` binding**|**Lexically binds `this`** (inherits from surrounding scope)|**Has its own `this`**|
|**Implicit Return**|**Yes** (for one-liners)|**No**, must use `return`|
|**Usable as a Constructor?**|❌ No|✅ Yes|
|**Hoisting**|❌ No (must be declared before use)|✅ Yes (function declarations are hoisted)|

---

## **🔹 Example: `this` Behavior in Arrow vs Regular Functions**

```js
const person = {
    name: "Achyuth",
    regularFunction: function() {
        console.log("Regular:", this.name);
    },
    arrowFunction: () => {
        console.log("Arrow:", this.name);
    }
};

person.regularFunction();  // "Regular: Achyuth"
person.arrowFunction();    // "Arrow: undefined"
```

✔️ **Arrow functions do not have their own `this`, they inherit from the surrounding scope**.

---

## **🚀 When to Use Arrow Functions?**

✔️ **Good for:**

- **Short functions**
- **Callbacks (`map, filter, reduce`)**
- **Avoiding `this` confusion**

❌ **Avoid for:**

- **Object methods** (since `this` won't refer to the object)
- **Constructors** (cannot use `new`)

# **🚀Understanding `this` Binding in Arrow vs Regular Functions 

In JavaScript, **`this` refers to the object that is calling the function**. However, how `this` is determined depends on whether you're using a **regular function** or an **arrow function**.

---

## **🔹 `this` in Regular Functions (`function`)**

- A **regular function** creates its **own `this`**.
- The value of `this` **depends on how the function is called**.

### **✅ Example 1: Regular Function in an Object**

```js
const person = {
    name: "Achyuth",
    greet: function() {
        console.log("Hello, " + this.name);
    }
};

person.greet();  // "Hello, Achyuth"
```

✔️ **Here, `this` refers to `person` because `greet()` is called on `person`**.

---

### **✅ Example 2: Losing `this` in a Regular Function**

```js
const person = {
    name: "Achyuth",
    greet: function() {
        setTimeout(function() {
            console.log("Hello, " + this.name);
        }, 1000);
    }
};

person.greet();  
// Output: "Hello, undefined" (or "Hello, " in browsers)
```

❌ **Problem:** `this` inside `setTimeout` refers to the global object (`window` in browsers, `undefined` in strict mode), **not `person`**.

---

## **🔹 `this` in Arrow Functions (`=>`)**

- **Arrow functions do NOT create their own `this`.**
- Instead, they **inherit `this` from the surrounding (parent) function**.

### **✅ Example 3: Fixing `this` with an Arrow Function**

```js
const person = {
    name: "Achyuth",
    greet: function() {
        setTimeout(() => {
            console.log("Hello, " + this.name);
        }, 1000);
    }
};

person.greet();  // "Hello, Achyuth"
```

✔️ **Here, `this` is inherited from `greet()`, which refers to `person`.**

---

### **🔹 Key Difference in Simple Terms**

|Feature|Regular Function (`function`)|Arrow Function (`=>`)|
|---|---|---|
|**How `this` Works**|Creates its own `this`|Inherits `this` from its surrounding function|
|**Inside Objects**|`this` refers to the object|`this` does NOT refer to the object|
|**Inside Callbacks (`setTimeout`, `map`)**|`this` may become `window` (or `undefined` in strict mode)|`this` stays the same as the outer function|

---

## **🚀 Summary (For Beginners)**

✔️ **Regular functions (`function`) create their own `this`, so `this` changes based on how the function is called.**  
✔️ **Arrow functions (`=>`) do not have their own `this` – they take `this` from where they are defined.**

👉 **Use regular functions when defining object methods.**  
👉 **Use arrow functions for callbacks (like `setTimeout`, `map`, `filter`) to avoid `this` issues.**


# **🚀Rest Operator (`...`) in JavaScript

The **rest operator (`...`)** allows a function to accept an **indefinite number of arguments** as an array. It is useful when working with functions that need to handle **multiple arguments dynamically**.

---

## **🔹 Syntax of Rest Operator**

```js
function myFunction(...restParams) {
    console.log(restParams);
}
```

- The `...` **rest operator** gathers multiple arguments into a **single array**.
- It **must be the last parameter** in the function.

---

## **🔹 Example 1: Using Rest Operator in Functions**

```js
function sum(...numbers) {
    return numbers.reduce((total, num) => total + num, 0);
}

console.log(sum(1, 2, 3, 4, 5)); // Output: 15
console.log(sum(10, 20));        // Output: 30
```

✔️ **All arguments are stored in an array (`numbers`) and processed with `.reduce()`**.

---

## **🔹 Example 2: Rest Operator with Normal Parameters**

```js
function introduce(firstName, lastName, ...hobbies) {
    console.log(`Hi, I am ${firstName} ${lastName}.`);
    console.log(`My hobbies are: ${hobbies.join(", ")}`);
}

introduce("Achyuth", "J", "Coding", "Gaming", "Traveling");
/*
Output:
Hi, I am Achyuth J.
My hobbies are: Coding, Gaming, Traveling
*/
```

✔️ **First two parameters are assigned normally, while the rest are collected in an array (`hobbies`).**

---

## **🔹 Example 3: Rest Operator in Destructuring**

The rest operator can also be used to collect **remaining elements** when destructuring arrays or objects.

### **✅ Rest in Array Destructuring**

```js
const numbers = [10, 20, 30, 40, 50];

const [first, second, ...rest] = numbers;
console.log(first);  // 10
console.log(second); // 20
console.log(rest);   // [30, 40, 50]
```

✔️ **First two elements are extracted, the rest go into an array.**

---

### **✅ Rest in Object Destructuring**

```js
const person = {
    name: "Achyuth",
    age: 25,
    country: "India",
    profession: "Developer"
};

const { name, age, ...otherDetails } = person;
console.log(name);         // "Achyuth"
console.log(age);          // 25
console.log(otherDetails); // { country: "India", profession: "Developer" }
```

✔️ **Extracts `name` and `age`, while `otherDetails` holds remaining properties.**

---

## **🚀 Key Points**

✔️ The **rest operator (`...`)** collects multiple arguments into an **array**.  
✔️ It **must be the last parameter** when used in functions.  
✔️ It works with **function arguments**, **array destructuring**, and **object destructuring**.  
✔️ **Different from the spread operator (`...`)**, which expands elements instead of collecting them.

# **🚀Spread Operator (`...`) in JavaScript**

### **🔹 What is the Spread Operator?**

The **spread operator (`...`)** is used to **expand elements** of an array, object, or iterable into individual elements. It is useful for **copying, merging, and passing multiple values**.

---

## **🔹 1. Spread in Arrays**

### ✅ **Copying an Array (Shallow Copy)**

```js
const numbers = [1, 2, 3];
const copy = [...numbers];

console.log(copy); // Output: [1, 2, 3]
```

✔️ **Creates a new array** without modifying the original.

---

### ✅ **Merging Arrays**

```js
const arr1 = [1, 2];
const arr2 = [3, 4];
const merged = [...arr1, ...arr2];

console.log(merged); // Output: [1, 2, 3, 4]
```

✔️ The spread operator **joins arrays without modifying them**.

---

### ✅ **Adding Elements to an Array**

```js
const nums = [2, 3, 4];
const newNums = [1, ...nums, 5];

console.log(newNums); // Output: [1, 2, 3, 4, 5]
```

✔️ **Adds elements dynamically** without affecting the original array.

---

## **🔹 2. Spread in Objects**

### ✅ **Copying an Object (Shallow Copy)**

```js
const user = { name: "Achyuth", age: 25 };
const copyUser = { ...user };

console.log(copyUser); // Output: { name: "Achyuth", age: 25 }
```

✔️ **Creates a new object** without modifying the original.

---

### ✅ **Merging Objects**

```js
const user = { name: "Achyuth" };
const details = { age: 25, city: "Kollam" };

const mergedUser = { ...user, ...details };

console.log(mergedUser); 
// Output: { name: "Achyuth", age: 25, city: "Kollam" }
```

✔️ **Combines multiple objects** into one.

---

### ✅ **Overriding Properties**

```js
const user = { name: "Achyuth", age: 25 };
const updatedUser = { ...user, age: 26 }; // Overriding age

console.log(updatedUser); // Output: { name: "Achyuth", age: 26 }
```

✔️ **Later properties override earlier ones**.

---

## **🔹 3. Spread in Function Arguments**

### ✅ **Passing an Array as Arguments**

```js
const numbers = [10, 20, 30];

function sum(a, b, c) {
    return a + b + c;
}

console.log(sum(...numbers)); // Output: 60
```

✔️ The spread operator **expands the array into separate arguments**.

---

## **🔹 4. Difference Between Spread (`...`) and Rest (`...`)**

|Feature|Spread (`...`)|Rest (`...`)|
|---|---|---|
|**Usage**|Expands elements|Gathers elements|
|**Where Used?**|Arrays, Objects, Function Arguments|Function Parameters|
|**Example**|`const copy = [...arr]`|`function sum(...nums) {}`|

✔️ **Spread extracts values, while Rest collects values!**

---

## **🚀 Summary**

✔️ **Copies arrays & objects**  
✔️ **Merges arrays & objects**  
✔️ **Passes array values as function arguments**  
✔️ **Simplifies coding and improves readability**

Let me know if you need more details! 🚀
# **🚀Deep Copy vs Shallow Copy in JavaScript**

When copying objects or arrays in JavaScript, there are two types of copies: **shallow copy** and **deep copy**. Understanding the difference is important to avoid unintended changes in data.

---

## **🔹 What is a Shallow Copy?**

A **shallow copy** creates a new object, but it **copies only the reference** of nested objects or arrays.

- Changes in the original object's nested elements **will affect the copied object** (because they both point to the same reference).

### **✅ Example of Shallow Copy**

```js
const original = {
    name: "Achyuth",
    details: {
        age: 25,
        city: "Kollam"
    }
};

// Creating a shallow copy using spread operator
const shallowCopy = { ...original };

// Modifying the nested object
shallowCopy.details.city = "Pattaya";

console.log(original.details.city);  // "Pattaya" (also changed!)
console.log(shallowCopy.details.city); // "Pattaya"
```

✔️ **The nested `details` object is still shared between `original` and `shallowCopy`**.  
❌ **Changing `shallowCopy.details.city` also changes `original.details.city`**.

### **🛠 Ways to Create a Shallow Copy**

- **Spread Operator (`{ ...obj }`)**
- **`Object.assign({}, obj)`**
- **`Array.prototype.slice()`** (for arrays)
- **`Array.prototype.concat()`** (for arrays)

---

## **🔹 What is a Deep Copy?**

A **deep copy** creates a completely independent copy, including all nested objects and arrays.

- Changes in the copied object **do not affect the original object**.

### **✅ Example of Deep Copy**

```js
const original = {
    name: "Achyuth",
    details: {
        age: 25,
        city: "Kollam"
    }
};

// Creating a deep copy using JSON methods
const deepCopy = JSON.parse(JSON.stringify(original));

// Modifying the nested object
deepCopy.details.city = "Pattaya";

console.log(original.details.city);  // "Kollam" (unchanged)
console.log(deepCopy.details.city);  // "Pattaya"
```

✔️ **Now, modifying `deepCopy.details.city` does NOT affect `original.details.city`**.

### **🛠 Ways to Create a Deep Copy**

1. **`JSON.parse(JSON.stringify(obj))`** ✅ (Simple, but loses functions & special values like `undefined`)
2. **Lodash's `cloneDeep(obj)`** ✅ (Best for all data types)
3. **Recursion (Manually copying each property)** ✅ (Flexible, but complex)
4. **Structured Clone API (`structuredClone(obj)`)** ✅ (Best modern method, supports all types)

---

## **🔹 Key Differences**

|Feature|Shallow Copy|Deep Copy|
|---|---|---|
|**Nested Objects**|**Copied by reference** (shared)|**Completely cloned** (independent)|
|**Modification Effect**|Changes in nested elements affect both copies|Changes in one copy do not affect the other|
|**Methods**|`Object.assign()`, spread operator `{ ...obj }`|`JSON.parse(JSON.stringify())`, `structuredClone()`, `_.cloneDeep()`|

---

## **🚀 Summary**

✔️ **Use shallow copy** when working with simple objects without nested structures.  
✔️ **Use deep copy** when you want to ensure that changes to the copy do not affect the original object.

# **🚀Object Literals in JavaScript**

### **🔹 What Are Object Literals?**

Object literals are a simple way to create objects in JavaScript using curly braces `{}`. They store key-value pairs and are widely used for **structuring data**.

---

## **🔹 1. Basic Object Literal Syntax**

```js
const person = {
    name: "Achyuth",
    age: 25,
    city: "Kollam"
};

console.log(person.name);  // Output: Achyuth
console.log(person.age);   // Output: 25
```

✔️ Uses `{ key: value }` format to create an object.

---

## **🔹 2. Shorthand Property Names**

If a variable has the same name as a key, you can **omit** the key name.

```js
const name = "Achyuth";
const age = 25;

const user = { name, age }; // Same as { name: name, age: age }

console.log(user); // Output: { name: 'Achyuth', age: 25 }
```

✔️ **Shortens code** and makes it cleaner.

---

## **🔹 3. Adding Methods to Objects**

```js
const user = {
    name: "Achyuth",
    greet() {  
        console.log(`Hello, my name is ${this.name}`);
    }
};

user.greet(); // Output: Hello, my name is Achyuth
```

✔️ **Method shorthand (`greet() {}`)** makes it concise.

---

## **🔹 4. Computed Property Names**

You can use **dynamic keys** inside objects.

```js
const key = "score";

const student = {
    name: "Yadav",
    [key]: 95
};

console.log(student.score); // Output: 95
```

✔️ **Dynamically sets a key name using a variable**.

---

## **🔹 5. Nesting Objects**

```js
const person = {
    name: "Mahindra",
    address: {
        city: "Pattaya",
        country: "Thailand"
    }
};

console.log(person.address.city); // Output: Pattaya
```

✔️ Objects **can contain other objects** inside them.

---

## **🔹 6. Merging Objects with Spread (`...`)**

```js
const obj1 = { a: 1, b: 2 };
const obj2 = { c: 3, d: 4 };

const merged = { ...obj1, ...obj2 };

console.log(merged); // Output: { a: 1, b: 2, c: 3, d: 4 }
```

✔️ **The spread operator (`...`) merges multiple objects**.

---

## **🔹 7. Checking if a Key Exists**

```js
const user = { name: "Achyuth", age: 25 };

console.log("age" in user); // Output: true
console.log(user.hasOwnProperty("city")); // Output: false
```

✔️ **Use `"key" in object` or `hasOwnProperty()`** to check if a key exists.

---

## **🚀 Summary**

✔️ **Object literals** make object creation simple  
✔️ Supports **shorthand properties** and **computed keys**  
✔️ Allows **methods, nesting, and merging**

# **🚀Array Destructuring in JavaScript**

### **🔹 What is Array Destructuring?**

Array destructuring is a **quick way to extract values** from an array and assign them to variables in a **single line**.

---

## **🔹 1. Basic Array Destructuring**

```js
const numbers = [10, 20, 30];

const [a, b, c] = numbers;

console.log(a); // Output: 10
console.log(b); // Output: 20
console.log(c); // Output: 30
```

✔️ Extracts values from the array **directly into variables**.

---

## **🔹 2. Skipping Elements**

You can **skip** array elements by leaving an empty space.

```js
const numbers = [10, 20, 30, 40];

const [first, , third] = numbers;

console.log(first);  // Output: 10
console.log(third);  // Output: 30
```

✔️ The second element **(20)** is skipped.

---

## **🔹 3. Default Values**

If an array doesn’t have enough elements, you can **set default values**.

```js
const numbers = [10];

const [a, b = 20, c = 30] = numbers;

console.log(a); // Output: 10
console.log(b); // Output: 20 (default used)
console.log(c); // Output: 30 (default used)
```

✔️ **Default values** are used **when no value is available**.

---

## **🔹 4. Swapping Variables Without a Temporary Variable**

```js
let x = 5, y = 10;

[x, y] = [y, x]; // Swap values

console.log(x); // Output: 10
console.log(y); // Output: 5
```

✔️ **No need for a temporary variable!** Just use destructuring.

---

## **🔹 5. Destructuring with Rest (`...`) Operator**

You can use the **rest operator (`...`)** to collect the remaining elements into an array.

```js
const numbers = [1, 2, 3, 4, 5];

const [first, second, ...rest] = numbers;

console.log(first);  // Output: 1
console.log(second); // Output: 2
console.log(rest);   // Output: [3, 4, 5]
```

✔️ The `rest` variable **collects the remaining values** as an array.

---

## **🔹 6. Nested Array Destructuring**

```js
const colors = [["red", "green"], ["blue", "yellow"]];

const [[firstColor, secondColor], [thirdColor]] = colors;

console.log(firstColor);  // Output: red
console.log(thirdColor);  // Output: blue
```

✔️ Destructuring **works with nested arrays** too!

---

## **🚀 Summary**

✔️ Extracts **array elements into variables easily**  
✔️ Supports **skipping elements & default values**  
✔️ Helps in **swapping variables & working with rest (`...`)**  
✔️ **Works with nested arrays**

# **🚀Object Destructuring in JavaScript**

### **🔹 What is Object Destructuring?**

Object destructuring is a **quick way to extract values** from objects and assign them to variables in a **single step**.

---

## **🔹 1. Basic Object Destructuring**

```js
const person = { name: "Achyuth", age: 25, city: "Kollam" };

const { name, age, city } = person;

console.log(name); // Output: Achyuth
console.log(age);  // Output: 25
console.log(city); // Output: Kollam
```

✔️ **Extracts object properties into variables** with the **same names**.

---

## **🔹 2. Changing Variable Names**

You can rename properties while destructuring.

```js
const person = { name: "Achyuth", age: 25 };

const { name: fullName, age: years } = person;

console.log(fullName); // Output: Achyuth
console.log(years);    // Output: 25
```

✔️ **`name` is stored as `fullName`, `age` as `years`**.

---

## **🔹 3. Default Values**

If a property is **missing**, you can assign a **default value**.

```js
const user = { name: "Achyuth" };

const { name, age = 30 } = user;

console.log(name); // Output: Achyuth
console.log(age);  // Output: 30 (default used)
```

✔️ If `age` doesn’t exist in `user`, it defaults to `30`.

---

## **🔹 4. Nested Object Destructuring**

You can extract **nested object properties**.

```js
const person = {
    name: "Achyuth",
    address: { city: "Pattaya", country: "Thailand" }
};

const { address: { city, country } } = person;

console.log(city);    // Output: Pattaya
console.log(country); // Output: Thailand
```

✔️ **Directly accesses nested properties** without needing `person.address.city`.

---

## **🔹 5. Using Rest (`...`) with Object Destructuring**

```js
const user = { name: "Achyuth", age: 25, city: "Kollam", country: "India" };

const { name, age, ...rest } = user;

console.log(name); // Output: Achyuth
console.log(age);  // Output: 25
console.log(rest); // Output: { city: "Kollam", country: "India" }
```

✔️ `...rest` **gathers remaining properties** into an object.

---

## **🔹 6. Destructuring in Function Parameters**

You can **directly extract object properties** inside function parameters.

```js
function displayUser({ name, age }) {
    console.log(`Name: ${name}, Age: ${age}`);
}

const user = { name: "Achyuth", age: 25, city: "Kollam" };

displayUser(user); // Output: Name: Achyuth, Age: 25
```

✔️ **No need to access `user.name` or `user.age` separately**.

---

## **🚀 Summary**

✔️ **Extracts object properties into variables**  
✔️ Supports **renaming, default values, and rest (`...`)**  
✔️ Works with **nested objects**  
✔️ **Simplifies function parameters**

Let me know if you need more details! 🚀




