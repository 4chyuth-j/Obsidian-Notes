# Read this documentation first:  https://www.geeksforgeeks.org/javascript/introduction-object-oriented-programming-javascript/
# What Is a Programming Paradigm?

**Programming Paradigm** — it's just a **style or way of thinking** about how to write and structure your code. Think of it like different approaches or mindsets to solve a problem using programming.


A **programming paradigm** is a **model** or **method** for solving problems using programming. It's like choosing a specific **toolbox** or **philosophy** to write code.

Just like in cooking:

- Some people like baking (strict measurements),
    
- Some like freestyle cooking (throw ingredients in),
    
- Some use one pot, others use many pans...
    

Same with coding — different styles/paradigms.

---

## 🔑 Common Types of Programming Paradigms

Here are some major ones you’ll come across:

---

### 1. **Imperative Programming**

**Think: “Do this step-by-step”**

- You give the computer exact instructions on _how_ to do something.
    
- Like a cooking recipe: "Chop onions → Heat oil → Add onions → Fry"
    

🧾 Example:

```js
let sum = 0;
for(let i = 1; i <= 5; i++) {
  sum += i;
}
console.log(sum); // 15
```

You are telling the computer: "Start from 1, go to 5, keep adding to sum."

---

### 2. **Declarative Programming**

**Think: “Tell what you want, not how”**

- You just describe _what_ you want, and the system figures out _how_ to do it.
    

🧾 Example (SQL):

```sql
SELECT name FROM students WHERE grade = 'A';
```

You don’t care how it finds those names — just give me all ‘A’ grade students.

Also seen in **React**: You declare the UI — not the steps to build it.

---

### 3. **Object-Oriented Programming (OOP)**

**Think: “Group code as real-world objects”**

- You break the program into **objects** like `Car`, `Student`, or `BankAccount`.
    
- Each object has **properties** (data) and **methods** (actions).
    

🧾 Example:

```js
class Car {
  constructor(brand) {
    this.brand = brand;
  }

  drive() {
    console.log(this.brand + " is driving");
  }
}
```

You think in **nouns** (Car, User), and attach behavior to them.

---

### 4. **Functional Programming**

**Think: “Use functions like math”**

- Focuses on **pure functions** — no side effects.
    
- No changing variables. Use **immutable** data.
    
- Avoid loops, use recursion or array methods (`map`, `filter`, `reduce`).
    

🧾 Example:

```js
const numbers = [1, 2, 3, 4];
const doubled = numbers.map(n => n * 2); // [2, 4, 6, 8]
```

Functional style is popular in React, JavaScript, and Python.

---

### 5. **Procedural Programming**

**Think: “Break into reusable steps (procedures/functions)”**

- A type of imperative programming.
    
- Code is organized into **procedures** (functions).
    

🧾 Example:

```js
function greet(name) {
  console.log("Hello " + name);
}

greet("Achyuth");
```

This was the common way in C language.

---

## 🤔 Why Should You Care?

Different problems suit different styles.

- Games → often use **OOP**
    
- Web UI (like React) → **Declarative + Functional**
    
- Data queries → **Declarative (SQL)**
    
- Embedded systems → **Procedural**
    

Knowing multiple paradigms = **better problem solving**.

---

## 🧠 TL;DR:

|Paradigm|Core Idea|Example|
|---|---|---|
|Imperative|Tell **how** to do it|For loops, step-by-step|
|Declarative|Tell **what** to do|SQL, React|
|OOP|Use **objects** and **classes**|Java, Python OOP|
|Functional|Use **pure functions** and no side effects|JavaScript `map`, `reduce`|
|Procedural|Break into **functions**|C, early Python|

---

If you want, I can make a **real-world analogy chart** or **mindmap-style image** for these too!