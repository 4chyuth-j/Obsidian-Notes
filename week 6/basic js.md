# 🚀Array methods

- sort
- reverse
- pop
- push
- shift 
- unshift
- concat
- join
- slice 
- splice
- isArray
- indexOf
- lastIndexof
- toArray
- valueOf
- fill


## **1. `sort()` – Sorting an Array**

The **`sort()`** method sorts the elements of an array **in place** and **converts them to strings by default**, sorting them lexicographically (dictionary order).

### **🔹 Sorting Strings (Default Behavior)**

```js
const fruits = ["banana", "apple", "cherry", "date"];
fruits.sort();
console.log(fruits);
// Output: [ 'apple', 'banana', 'cherry', 'date' ]
```

### **🔹 Sorting Numbers (Needs a Compare Function)**

By default, **`sort()` does not work correctly for numbers** because it treats them as strings.

```js
const numbers = [10, 5, 20, 2];
numbers.sort(); 
console.log(numbers);
// Output: [10, 2, 20, 5] ❌ (Incorrect because it's sorted as strings)
```

### ✅ **Fix: Use a Compare Function**

```js
numbers.sort((a, b) => a - b);
console.log(numbers);
// Output: [2, 5, 10, 20] ✅ (Sorted correctly)
```

- **Ascending Order**: `(a, b) => a - b`
- **Descending Order**: `(a, b) => b - a`

### **🔹 Sorting Objects by Property**

```js
const users = [
  { name: "Achyuth", age: 25 },
  { name: "Mahindra", age: 22 },
  { name: "Yadav", age: 28 }
];

users.sort((a, b) => a.age - b.age);
console.log(users);
/*
Output:
[
  { name: 'Mahindra', age: 22 },
  { name: 'Achyuth', age: 25 },
  { name: 'Yadav', age: 28 }
]
*/
```

---

## **2. `reverse()` – Reversing an Array**

The **`reverse()`** method reverses the elements **in place**.

```js
const numbers = [1, 2, 3, 4, 5];
numbers.reverse();
console.log(numbers);
// Output: [5, 4, 3, 2, 1]
```

### **🔹 Sorting in Descending Order using `sort()` and `reverse()`**

```js
const numbers = [10, 5, 20, 2];
numbers.sort((a, b) => a - b).reverse();
console.log(numbers);
// Output: [20, 10, 5, 2]
```


## **3. `push()` – Adds Elements to the End of an Array**

The **`push()`** method adds one or more elements to the **end** of an array and returns the **new length** of the array.

### **🔹 Example**

```js
const fruits = ["apple", "banana"];
fruits.push("cherry");
console.log(fruits); // Output: [ 'apple', 'banana', 'cherry' ]
```

### **🔹 Pushing Multiple Elements**

```js
const numbers = [1, 2, 3];
numbers.push(4, 5, 6);
console.log(numbers); // Output: [ 1, 2, 3, 4, 5, 6 ]
```

### **🔹 `push()` Returns the New Length**

```js
const arr = [10, 20];
const newLength = arr.push(30);
console.log(arr); // Output: [10, 20, 30]
console.log(newLength); // Output: 3
```

---

## **4. `pop()` – Removes the Last Element**

The **`pop()`** method removes the **last element** from an array and returns **that removed element**.

### **🔹 Example**

```js
const fruits = ["apple", "banana", "cherry"];
const lastFruit = fruits.pop();
console.log(fruits); // Output: [ 'apple', 'banana' ]
console.log(lastFruit); // Output: 'cherry' (removed element)
```

### **🔹 Using `pop()` on an Empty Array**

If the array is empty, `pop()` returns `undefined`.

```js
const emptyArr = [];
console.log(emptyArr.pop()); // Output: undefined
```

---

### **Summary Table**

|Method|Purpose|Modifies Original Array?|Returns|
|---|---|---|---|
|`push()`|Adds element(s) to the end|✅ Yes|New length of the array|
|`pop()`|Removes the last element|✅ Yes|The removed element|

---

### **Real-World Example (Stack Implementation)**

The `push()` and `pop()` methods are commonly used in **stack data structures**.

```js
const stack = [];

stack.push(1);
stack.push(2);
stack.push(3);
console.log(stack); // Output: [1, 2, 3]

const lastElement = stack.pop();
console.log(lastElement); // Output: 3
console.log(stack); // Output: [1, 2]
```


## **5. `unshift()` – Adds Elements to the Beginning**

The **`unshift()`** method **adds** one or more elements to the **beginning** of an array and returns the **new length** of the array.

### **🔹 Example**

```js
const fruits = ["banana", "cherry"];
fruits.unshift("apple"); 
console.log(fruits); // Output: [ 'apple', 'banana', 'cherry' ]
```

### **🔹 Adding Multiple Elements**

```js
const numbers = [3, 4, 5];
numbers.unshift(1, 2);
console.log(numbers); // Output: [1, 2, 3, 4, 5]
```

### **🔹 `unshift()` Returns the New Length**

```js
const arr = [10, 20];
const newLength = arr.unshift(5);
console.log(arr); // Output: [5, 10, 20]
console.log(newLength); // Output: 3
```

---

## **6. `shift()` – Removes the First Element**

The **`shift()`** method **removes** the **first element** from an array and returns **that removed element**.

### **🔹 Example**

```js
const fruits = ["apple", "banana", "cherry"];
const firstFruit = fruits.shift();
console.log(fruits); // Output: [ 'banana', 'cherry' ]
console.log(firstFruit); // Output: 'apple' (removed element)
```

### **🔹 Using `shift()` on an Empty Array**

If the array is empty, `shift()` returns `undefined`.

```js
const emptyArr = [];
console.log(emptyArr.shift()); // Output: undefined
```

---

### **Summary Table**

|Method|Purpose|Modifies Original Array?|Returns|
|---|---|---|---|
|`unshift()`|Adds element(s) to the beginning|✅ Yes|New length of the array|
|`shift()`|Removes the first element|✅ Yes|The removed element|

---

### **Real-World Example (Queue Implementation)**

The `shift()` and `unshift()` methods are commonly used in **queue data structures** (FIFO – First In, First Out).

```js
const queue = [];

queue.unshift("Customer 1");
queue.unshift("Customer 2");
queue.unshift("Customer 3");
console.log(queue); // Output: ['Customer 3', 'Customer 2', 'Customer 1']

const servedCustomer = queue.shift();
console.log(servedCustomer); // Output: 'Customer 3'
console.log(queue); // Output: ['Customer 2', 'Customer 1']
```


## **7. `concat()` – Merging Arrays**

The **`concat()`** method merges two or more arrays **without modifying the original arrays** and returns a new array.

### **🔹 Example: Concatenating Two Arrays**

```js
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];

const merged = arr1.concat(arr2);
console.log(merged); // Output: [1, 2, 3, 4, 5, 6]
console.log(arr1); // Output: [1, 2, 3] (Original remains unchanged)
```

### **🔹 Concatenating Multiple Arrays**

```js
const arr1 = ["a", "b"];
const arr2 = ["c", "d"];
const arr3 = ["e", "f"];

const combined = arr1.concat(arr2, arr3);
console.log(combined); // Output: [ 'a', 'b', 'c', 'd', 'e', 'f' ]
```

### **🔹 Concatenating with Values**

```js
const numbers = [1, 2, 3];
const newArray = numbers.concat(4, 5, [6, 7]);

console.log(newArray); // Output: [1, 2, 3, 4, 5, 6, 7]
```

---

## **8. `join()` – Convert an Array to a String**

The **`join()`** method **converts an array into a string**, with elements separated by a specified delimiter.

### **🔹 Example: Default `join()` (Comma-Separated)**

```js
const fruits = ["apple", "banana", "cherry"];
const result = fruits.join();
console.log(result); // Output: "apple,banana,cherry"
```

### **🔹 Using a Custom Separator**

```js
const words = ["Hello", "world"];
console.log(words.join(" ")); // Output: "Hello world"
console.log(words.join("-")); // Output: "Hello-world"
console.log(words.join("")); // Output: "Helloworld"
```

### **🔹 Joining Numbers**

```js
const numbers = [1, 2, 3, 4];
console.log(numbers.join(" -> ")); // Output: "1 -> 2 -> 3 -> 4"
```

---

### **Key Differences Between `concat()` and `join()`**

|Method|Purpose|Modifies Original Array?|Returns|
|---|---|---|---|
|`concat()`|Merges arrays|❌ No|A new array|
|`join()`|Converts array to string|❌ No|A string|


## **9. `slice()` – Extracts a Portion of an Array**

The **`slice(start, end)`** method returns a **new array** containing elements from `start` to `end - 1` (end index is not included).  
🛑 **Does NOT modify the original array**.

### **🔹 Example: Extracting Elements**

```js
const numbers = [1, 2, 3, 4, 5];
const sliced = numbers.slice(1, 4); 
console.log(sliced); // Output: [2, 3, 4] (Indexes 1 to 3)
console.log(numbers); // Output: [1, 2, 3, 4, 5] (Original array unchanged)
```

### **🔹 Omitting the `end` Parameter**

```js
const fruits = ["apple", "banana", "cherry", "date"];
console.log(fruits.slice(1));  // Output: ["banana", "cherry", "date"] (From index 1 to end)
```

### **🔹 Using Negative Indexes**

```js
const nums = [10, 20, 30, 40, 50];
console.log(nums.slice(-3));  // Output: [30, 40, 50] (Last 3 elements)
console.log(nums.slice(-4, -1)); // Output: [20, 30, 40] (Excludes last element)
```

---

## **10. `splice()` – Modifies an Array (Remove, Replace, Add)**

The **`splice(start, deleteCount, item1, item2, ...)`** method:  
✅ Removes `deleteCount` elements from `start`.  
✅ Adds `item1, item2, ...` at `start`.  
✅ **Modifies the original array** and returns the removed elements.

### **🔹 Removing Elements**

```js
const numbers = [1, 2, 3, 4, 5];
const removed = numbers.splice(1, 2); 
console.log(numbers); // Output: [1, 4, 5] (2 and 3 removed)
console.log(removed); // Output: [2, 3] (Removed elements)
```

### **🔹 Adding Elements**

```js
const colors = ["red", "green", "blue"];
colors.splice(1, 0, "yellow", "purple"); 
console.log(colors); // Output: ["red", "yellow", "purple", "green", "blue"]
```

### **🔹 Replacing Elements**

```js
const names = ["Achyuth", "Mahindra", "Yadav"];
names.splice(1, 1, "Rahul"); // Replace "Mahindra" with "Rahul"
console.log(names); // Output: ["Achyuth", "Rahul", "Yadav"]
```

---

### **Key Differences Between `slice()` and `splice()`**

|Method|Purpose|Modifies Original Array?|Returns|
|---|---|---|---|
|`slice()`|Extracts part of an array|❌ No|A new array|
|`splice()`|Removes, replaces, or adds elements|✅ Yes|Removed elements|



## **11.`Array.isArray()` Method in JavaScript**

The **`Array.isArray()`** method is used to check whether a given value is an **array** or not.  
It returns a **boolean** (`true` or `false`).

---

### **🔹 Syntax**

```js
Array.isArray(value);
```

✅ Returns **`true`** if `value` is an array.  
❌ Returns **`false`** if `value` is not an array.

---

### **🔹 Examples**

### **Checking Arrays**

```js
console.log(Array.isArray([1, 2, 3])); // Output: true
console.log(Array.isArray(["apple", "banana"])); // Output: true
console.log(Array.isArray(new Array(5))); // Output: true
```

### **Checking Non-Array Values**

```js
console.log(Array.isArray("Hello")); // Output: false
console.log(Array.isArray({ key: "value" })); // Output: false
console.log(Array.isArray(123)); // Output: false
console.log(Array.isArray(null)); // Output: false
console.log(Array.isArray(undefined)); // Output: false
```

### **Checking `typeof` vs `Array.isArray()`**

```js
console.log(typeof [1, 2, 3]); // Output: "object" (arrays are objects)
console.log(Array.isArray([1, 2, 3])); // Output: true (correct way to check for an array)
```

---

### **🔹 Why Use `Array.isArray()`?**

1. **Reliable Check:** Arrays in JavaScript are a type of object, so `typeof` doesn't work correctly.
2. **Avoid Errors:** Ensures you're working with an array before using array methods (`push`, `map`, etc.).
3. **Cross-Environment Support:** Works correctly in all JavaScript environments, including different JavaScript engines.

---


## **12. `indexOf()` – Finds First Occurrence**

The **`indexOf(element, startIndex)`** method returns the **first index** where `element` is found.  
If the element is **not found**, it returns `-1`.

### **🔹 Syntax**

```js
array.indexOf(element, startIndex);
```

- `element` – The value to search for.
- `startIndex` (optional) – Where to start searching (default is `0`).

### **🔹 Example**

```js
const numbers = [10, 20, 30, 40, 50, 20];

console.log(numbers.indexOf(20)); // Output: 1 (first occurrence)
console.log(numbers.indexOf(50)); // Output: 4
console.log(numbers.indexOf(100)); // Output: -1 (not found)
```

### **🔹 Using `startIndex`**

```js
const numbers = [10, 20, 30, 40, 50, 20];

console.log(numbers.indexOf(20, 2)); // Output: 5 (starts searching from index 2)
```

---

## **13. `lastIndexOf()` – Finds Last Occurrence**

The **`lastIndexOf(element, startIndex)`** method returns the **last index** where `element` is found.  
If the element is **not found**, it returns `-1`.

### **🔹 Syntax**

```js
array.lastIndexOf(element, startIndex);
```

- `element` – The value to search for.
- `startIndex` (optional) – Where to start searching (default is the end of the array).

### **🔹 Example**

```js
const numbers = [10, 20, 30, 40, 50, 20];

console.log(numbers.lastIndexOf(20)); // Output: 5 (last occurrence)
console.log(numbers.lastIndexOf(50)); // Output: 4
console.log(numbers.lastIndexOf(100)); // Output: -1 (not found)
```

### **🔹 Using `startIndex`**

```js
const numbers = [10, 20, 30, 40, 50, 20];

console.log(numbers.lastIndexOf(20, 4)); // Output: 1 (starts searching from index 4 backwards)
```

---

### **Key Differences Between `indexOf()` and `lastIndexOf()`**

|Method|Purpose|Searches From|Returns|
|---|---|---|---|
|`indexOf()`|Finds first occurrence|Left to right|First matching index (or `-1`)|
|`lastIndexOf()`|Finds last occurrence|Right to left|Last matching index (or `-1`)|



## **14. `includes()` Method in JavaScript**

The **`includes()`** method checks if an array contains a specific element and returns a **boolean (`true` or `false`)**.

✅ **Returns `true`** if the element is found.  
❌ **Returns `false`** if the element is not found.

---

### **🔹 Syntax**

```js
array.includes(element, startIndex);
```

- `element` – The value to search for.
- `startIndex` (optional) – The index from where the search starts (default is `0`).

---

### **🔹 Example: Basic Usage**

```js
const fruits = ["apple", "banana", "cherry"];

console.log(fruits.includes("banana")); // Output: true
console.log(fruits.includes("grape")); // Output: false
```

---

### **🔹 Using `startIndex`**

```js
const numbers = [10, 20, 30, 40, 50];

console.log(numbers.includes(20, 2)); // Output: false (starts searching from index 2)
console.log(numbers.includes(40, 2)); // Output: true (40 exists at index 3)
```

---

### **🔹 Checking for `NaN` (Unlike `indexOf()`)**

```js
const values = [1, 2, NaN, 4];

console.log(values.includes(NaN)); // Output: true
console.log(values.indexOf(NaN)); // Output: -1 (indexOf cannot detect NaN)
```

💡 **`includes()` can find `NaN`, but `indexOf()` cannot!**

---

### **Key Differences: `includes()` vs `indexOf()`**

|Method|Purpose|Returns|Can Detect `NaN`?|
|---|---|---|---|
|`includes()`|Checks if an element exists|`true` or `false`|✅ Yes|
|`indexOf()`|Finds the first index of an element|Index (or `-1` if not found)|❌ No|


## **15. `some()` – Checks If Any Element Matches**

The **`some(callback)`** method tests whether **at least one** element in the array **meets the condition**.  
🔹 Returns `true` if any element matches.  
🔹 Returns `false` if **no** element matches.

### **🔹 Syntax**

```js
array.some((element, index, array) => condition);
```

### **🔹 Example: Checking for Even Numbers**

```js
const numbers = [1, 3, 5, 8];

const hasEven = numbers.some(num => num % 2 === 0);
console.log(hasEven); // Output: true (because 8 is even)
```

### **🔹 Example: Checking for Negative Numbers**

```js
const numbers = [2, 4, 6, -3];

console.log(numbers.some(num => num < 0)); // Output: true (because -3 is negative)
```

---

## **16. `every()` – Checks If All Elements Match**

The **`every(callback)`** method tests whether **all** elements in the array **meet the condition**.  
🔹 Returns `true` only if **all** elements match.  
🔹 Returns `false` if **any** element fails.

### **🔹 Syntax**

```js
array.every((element, index, array) => condition);
```

### **🔹 Example: Checking If All Numbers Are Even**

```js
const numbers = [2, 4, 6, 8];

const allEven = numbers.every(num => num % 2 === 0);
console.log(allEven); // Output: true (all numbers are even)
```

### **🔹 Example: Checking If All Numbers Are Positive**

```js
const numbers = [1, 2, 3, -4, 5];

console.log(numbers.every(num => num > 0)); // Output: false (because -4 is negative)
```

---

### **Key Differences Between `some()` and `every()`**

|Method|Purpose|Returns `true` If...|Stops Checking When...|
|---|---|---|---|
|`some()`|Checks if **at least one** element matches|**Any** element satisfies the condition|**First match is found**|
|`every()`|Checks if **all** elements match|**All** elements satisfy the condition|**First failure is found**|

---

### **🔹 Practical Use Cases**

✔ **`some()` for validation** (e.g., checking if any input is empty).  
✔ **`every()` for validation** (e.g., checking if all inputs are valid).


## **17. `find()` – Returns the First Matching Element**

The **`find(callback)`** method searches an array and returns the **first element** that satisfies the given condition.

### **🔹 Syntax**

```js
array.find((element, index, array) => condition);
```

### **🔹 Example: Finding the First Even Number**

```js
const numbers = [1, 3, 5, 8, 10];

const firstEven = numbers.find(num => num % 2 === 0);
console.log(firstEven); // Output: 8 (first even number found)
```

### **🔹 Example: Finding an Object in an Array**

```js
const users = [
    { name: "Achyuth", age: 25 },
    { name: "Yadav", age: 17 },
    { name: "Mahindra", age: 22 }
];

const user = users.find(user => user.age < 18);
console.log(user); // Output: { name: "Yadav", age: 17 } (first user under 18)
```

---

## **18. `findIndex()` – Returns the Index of the First Matching Element**

The **`findIndex(callback)`** method returns the **index** of the first element that satisfies the given condition.

### **🔹 Syntax**

```js
array.findIndex((element, index, array) => condition);
```

### **🔹 Example: Finding Index of First Even Number**

```js
const numbers = [1, 3, 5, 8, 10];

const evenIndex = numbers.findIndex(num => num % 2 === 0);
console.log(evenIndex); // Output: 3 (index of first even number: 8)
```

### **🔹 Example: Finding the Index of a Specific User**

```js
const users = [
    { name: "Achyuth", age: 25 },
    { name: "Yadav", age: 17 },
    { name: "Mahindra", age: 22 }
];

const index = users.findIndex(user => user.age < 18);
console.log(index); // Output: 1 (Yadav is at index 1)
```

---

### **Key Differences Between `find()` and `findIndex()`**

|Method|Purpose|Returns|When No Match Found|
|---|---|---|---|
|`find()`|Finds the first matching element|The element itself|`undefined`|
|`findIndex()`|Finds the index of the first matching element|The index|`-1`|


## **19. `filter()` Method in JavaScript – In Depth Explanation**

The **`filter()`** method is a **higher-order function** used to create a **new array** containing only the elements that satisfy a specified condition. It does **not modify the original array**.

✅ **Returns a new array** with matching elements.  
❌ **If no elements match**, it returns an **empty array** (`[]`).

---

### **🔹 How `filter()` Works Internally**

1. `filter()` iterates over each element in the array.
2. It applies the provided callback function to each element.
3. If the callback function **returns `true`**, the element is added to the new array.
4. If the callback function **returns `false`**, the element is skipped.
5. Once all elements are checked, `filter()` returns the **new array** with only the matching elements.

---

### **🔹 Syntax**

```js
array.filter((element, index, array) => condition);
```

- `element` – The current element being processed.
- `index` _(optional)_ – The index of the current element.
- `array` _(optional)_ – The full array being processed.

---

### **1. Basic Example – Filtering Even Numbers**

```js
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

const evenNumbers = numbers.filter(num => num % 2 === 0);
console.log(evenNumbers); // Output: [2, 4, 6, 8, 10]
```

💡 **How it works:**

- `num % 2 === 0` is checked for each number.
- If `true`, the number is included in the new array.
- If `false`, the number is skipped.

---

### **2. Filtering Objects – Getting Adults**

```js
const users = [
    { name: "Achyuth", age: 25 },
    { name: "Yadav", age: 17 },
    { name: "Mahindra", age: 22 },
    { name: "Raj", age: 15 }
];

const adults = users.filter(user => user.age >= 18);
console.log(adults);
/* Output:
[
    { name: "Achyuth", age: 25 },
    { name: "Mahindra", age: 22 }
]
*/
```

💡 **How it works:**

- `user.age >= 18` is checked for each object.
- If `true`, the object is included.
- If `false`, the object is skipped.

---

### **3. Filtering Strings – Words That Start With "A"**

```js
const words = ["apple", "banana", "cherry", "avocado", "blueberry"];

const aWords = words.filter(word => word.startsWith("a"));
console.log(aWords); // Output: ["apple", "avocado"]
```

💡 **How it works:**

- `.startsWith("a")` checks if a word starts with `"a"`.
- If `true`, it is included in the new array.

---

### **4. Removing Falsy Values (Truthy Filter)**

```js
const mixedArray = [0, 1, false, 2, "", 3, null, "hello", undefined, NaN];

const truthyValues = mixedArray.filter(Boolean);
console.log(truthyValues); // Output: [1, 2, 3, "hello"]
```

💡 **How it works:**

- `Boolean(value)` converts values to `true` (truthy) or `false` (falsy).
- Falsy values (`false`, `0`, `""`, `null`, `undefined`, `NaN`) are **removed**.

---

### **5. Filtering with Index Parameter**

You can also use the **index** inside the callback function.

```js
const numbers = [10, 20, 30, 40, 50];

const filteredNumbers = numbers.filter((num, index) => index % 2 === 0);
console.log(filteredNumbers); // Output: [10, 30, 50] (Only even index values)
```

💡 **How it works:**

- The filter keeps numbers where `index % 2 === 0`, meaning only elements at even indexes are included.

---

### **6. Filtering an Array of Objects Based on Multiple Conditions**

```js
const products = [
    { name: "Laptop", price: 1200, inStock: true },
    { name: "Phone", price: 800, inStock: false },
    { name: "Tablet", price: 600, inStock: true },
    { name: "Monitor", price: 300, inStock: true }
];

const affordableAndInStock = products.filter(product => product.price < 1000 && product.inStock);
console.log(affordableAndInStock);
/* Output:
[
    { name: "Tablet", price: 600, inStock: true },
    { name: "Monitor", price: 300, inStock: true }
]
*/
```

💡 **How it works:**

- Only products with `price < 1000` and `inStock === true` are included.

---

### **🔹 Key Differences: `filter()` vs. `find()` vs. `findIndex()`**

|Method|Purpose|Returns|When No Match Found|
|---|---|---|---|
|`filter()`|Finds **all** matching elements|A **new array** with matches|`[]` (empty array)|
|`find()`|Finds **only the first** matching element|The element itself|`undefined`|
|`findIndex()`|Finds the **index** of the first matching element|Index number|`-1`|

---

### **🔹 When to Use `filter()`**

✔ When you need **multiple matches**.  
✔ When you want to **remove unwanted elements**.  
✔ When working with **arrays of objects** (filtering based on properties).

---

### **🔹 Performance Considerations**

- **`filter()` runs for all elements**, even if the first few satisfy the condition.
- **If you only need the first match**, use `find()` instead for better performance.

---

### **Conclusion**

The **`filter()`** method is powerful for working with arrays when you need to find multiple elements that match a condition. It is especially useful for **searching, removing unwanted values, and filtering objects based on properties**.


## **20. toString() – Convert an Array or Object to a String**

The **`toString()`** method converts an array or object into a string representation.

### **How it Works**

- For **arrays**, `toString()` joins elements into a comma-separated string.
- `toString()` method **does not modify** the original array. It simply returns a string    representation of the array while keeping the original array unchanged.

- For **objects**, it usually returns `"[object Object]"` unless overridden.
- For **numbers, booleans, and strings**, it returns their string representation.

### **Syntax**

```js
array.toString();
object.toString();
```

### **Example: Array to String**

```js
const fruits = ["apple", "banana", "cherry"];
console.log(fruits.toString()); 
// Output: "apple,banana,cherry"
```

### **Example: Number to String**

```js
const num = 100;
console.log(num.toString()); 
// Output: "100"
```

### **Example: Object to String**

```js
const person = { name: "Achyuth", age: 25 };
console.log(person.toString()); 
// Output: "[object Object]"
```

💡 **To get a readable object string, use `JSON.stringify()`**

```js
console.log(JSON.stringify(person)); 
// Output: '{"name":"Achyuth","age":25}'
```

---

## **21. valueOf() – Get the Primitive Value of an Object**

The **`valueOf()`** method returns the **primitive value** of a number, string, boolean, or object wrapper.

### **How it Works**

- For **numbers, strings, booleans**, `valueOf()` extracts the raw primitive value.
- For **arrays and objects**, it usually returns the object itself.

### **Syntax**

```js
object.valueOf();
```

### **Example: Number Object to Primitive**

```js
const num = new Number(42);
console.log(num.valueOf()); 
// Output: 42 (not an object, just a number)
```

### **Example: String Object to Primitive**

```js
const str = new String("Hello");
console.log(str.valueOf()); 
// Output: "Hello"
```

### **Example: Array `valueOf()`**

```js
const arr = [10, 20, 30];
console.log(arr.valueOf()); 
// Output: [10, 20, 30] (same array)
```

### **Example: Custom Object Overriding `valueOf()`**

You can **customize** `valueOf()` for an object.

```js
const user = {
    name: "Achyuth",
    valueOf: function() {
        return this.name;
    }
};
console.log(user.valueOf()); 
// Output: "Achyuth"
```

---

## **22. fill() – Fill an Array with a Static Value**

The **`fill()`** method replaces all or part of an array with a specific value.

### **How it Works**

- It **modifies** the original array.
- You can **fill the entire array** or **only a part** of it using start and end indexes.

### **Syntax**

```js
array.fill(value, start, end);
```

- `value` – The value to insert.
- `start` _(optional)_ – Index where filling starts (default `0`).
- `end` _(optional)_ – Index where filling stops (**not included**, default `array.length`).

### **Example: Fill an Entire Array**

```js
const arr = [1, 2, 3, 4, 5];
arr.fill(0);
console.log(arr); 
// Output: [0, 0, 0, 0, 0]
```

### **Example: Fill a Portion of an Array**

```js
const arr = [1, 2, 3, 4, 5];
arr.fill(9, 1, 4);
console.log(arr); 
// Output: [1, 9, 9, 9, 5]
```

💡 **How it works:**

- Starts at index `1` and stops at index `4` (**not including `4`**).

### **Example: Creating a New Array with `fill()`**

```js
const newArray = new Array(5).fill("X");
console.log(newArray);
// Output: ["X", "X", "X", "X", "X"]
```

💡 **How it works:**

- `new Array(5)` creates an **empty array** of length `5`.
- `.fill("X")` fills all positions with `"X"`.

### **Example: Reset an Array**

```js
let data = [1, 2, 3, 4, 5];
data.fill(null);
console.log(data); 
// Output: [null, null, null, null, null]
```

💡 **Useful for resetting arrays** with `null`, `0`, or `""`.

---

### **Comparison Table**

|Method|Purpose|Works On|Example Output|
|---|---|---|---|
|`toString()`|Converts to a string|Arrays, objects|`"1,2,3"`|
|`valueOf()`|Gets primitive value|Numbers, strings, objects|`42`|
|`fill()`|Fills array with a value|Arrays|`[0, 0, 0, 0, 0]`|

---

### **When to Use Each?**

✅ **Use `toString()`** when you need a **string representation** of an array or object.  
✅ **Use `valueOf()`** to extract the **primitive value** of wrapper objects.  
✅ **Use `fill()`** to **initialize arrays, reset data, or replace values** in an array.

---




# **🚀String methods in js
## `toUpperCase()` and `toLowerCase()` in JavaScript**

- **`toUpperCase()`** → Converts all letters in a string to **uppercase**.
- **`toLowerCase()`** → Converts all letters in a string to **lowercase**.

#### **Example:**

```js
const text = "Hello World";

console.log(text.toUpperCase());  // "HELLO WORLD"
console.log(text.toLowerCase());  // "hello world"
```

✔️ **Does not modify the original string**  
✔️ **Useful for case-insensitive comparisons**


## **`includes()` in JavaScript**

The **`includes()`** method checks if a **string or array** contains a specific value and returns **`true`** or **`false`**.

#### **🔹 Syntax:**

```js
string.includes(searchValue, startIndex)  // For strings
array.includes(searchValue, fromIndex)   // For arrays
```

- `searchValue` → The value to search for.
- `startIndex / fromIndex` _(optional)_ → The position to start searching from (default: `0`).

---

### **🔹 Example 1: Using `includes()` with Strings**

```js
const text = "JavaScript is awesome";

console.log(text.includes("JavaScript"));  // true
console.log(text.includes("python"));      // false
console.log(text.includes("is", 5));       // true (search starts from index 5)
```

---
✔️ **Case-sensitive**  
✔️ **Returns `true` if found, otherwise `false`**  
✔️ **Works on both strings and arrays**

## **`startsWith()` and `endsWith()` in JavaScript**

These methods check whether a **string** begins or ends with a specific value and return **`true`** or **`false`**.

---

### **🔹 `startsWith()`**

Checks if a string **starts** with a specific substring.

#### **✅ Syntax:**

```js
string.startsWith(searchString, startPosition)
```

- `searchString` → The text to check.
- `startPosition` _(optional)_ → The index to start checking from (default: `0`).

#### **✅ Example:**

```js
const text = "Hello, JavaScript!";

console.log(text.startsWith("Hello"));  // true
console.log(text.startsWith("Java"));   // false
console.log(text.startsWith("Java", 7)); // true (search from index 7)
```

---

### **🔹 `endsWith()`**

Checks if a string **ends** with a specific substring.

#### **✅ Syntax:**

```js
string.endsWith(searchString, length)
```

- `searchString` → The text to check.
- `length` _(optional)_ → The length of the string to check within.

#### **✅ Example:**

```js
const text = "Hello, JavaScript!";

console.log(text.endsWith("!"));        // true
console.log(text.endsWith("Script!"));  // true
console.log(text.endsWith("Java", 10)); // true (checks only first 10 characters)
```

---

### **🚀 Key Points**

✔️ **Case-sensitive**  
✔️ **Returns `true` if found, otherwise `false`**  
✔️ **Useful for checking file extensions, prefixes, etc.**


## **`search()` Method in JavaScript**

The **`search()`** method finds the **position (index) of the first match** of a given substring or **regular expression** inside a string. If no match is found, it returns **`-1`**.

---

### **🔹 Syntax**

```js
string.search(searchValue)
```

- `searchValue` → A string or a **regular expression** to search for.

---

### **🔹 Example 1: Searching for a Word**

```js
const text = "JavaScript is powerful";

console.log(text.search("is"));   // 11 (index of "is")
console.log(text.search("hello")); // -1 (not found)
```

---

### **🔹 Example 2: Using Regular Expressions**

```js
const text = "I love JavaScript!";

console.log(text.search(/javaScript/i)); // 7 (case-insensitive search)
console.log(text.search(/\d/));         // -1 (no numbers in the string)
```

---

### **🚀 Key Points**

✔️ **Returns the index of the first match**  
✔️ **Returns `-1` if not found**  
✔️ **Supports regular expressions**  
✔️ **Case-sensitive by default** (use `/i` for case-insensitive search)

## **`match()` Method in JavaScript**

The **`match()`** method searches a string for a match against a **regular expression** and returns the **matches as an array**. If no match is found, it returns **`null`**.

---

### **🔹 Syntax**

```js
string.match(regexp)
```

- `regexp` → A **regular expression** to search for.
- If **no match** is found, it returns **`null`**.

---

### **🔹 Example 1: Finding a Word in a String**

```js
const text = "I love JavaScript!";

console.log(text.match("JavaScript")); 
// Output: ["JavaScript", index: 7, input: "I love JavaScript!", groups: undefined]

console.log(text.match("Python"));  
// Output: null (not found)
```

---

### **🔹 Example 2: Using Regular Expressions**

```js
const text = "JavaScript is amazing. I love JavaScript!";

// Find all occurrences of "JavaScript"
console.log(text.match(/JavaScript/g)); 
// Output: ["JavaScript", "JavaScript"]

// Case-insensitive search
console.log(text.match(/javascript/i)); 
// Output: ["JavaScript"]

// Find all vowels
console.log(text.match(/[aeiou]/gi));  
// Output: ["a", "a", "i", "i", "a", "a", "i", "I", "o", "e", "a", "a", "i"]
```

---

### **🚀 Key Points**

✔️ **Returns an array of matches**  
✔️ **Returns `null` if no match is found**  
✔️ **Supports regular expressions** (`/g` for multiple matches, `/i` for case-insensitive search)  
✔️ **Great for extracting specific text from a string**

## **`indexOf()` and `lastIndexOf()` 

These methods **search for a substring** inside a string and return the **position (index) of its occurrence**. If the substring is **not found**, they return **`-1`**.

---

### **🔹 `indexOf()` – First Occurrence**

Finds the **first occurrence** of a substring.

#### **✅ Syntax:**

```js
string.indexOf(searchValue, startIndex)
```

- `searchValue` → The substring to search for.
- `startIndex` _(optional)_ → The position to start searching from (default: `0`).

#### **✅ Example:**

```js
const text = "JavaScript is amazing!";

console.log(text.indexOf("is"));   // 11
console.log(text.indexOf("a"));    // 1 (first 'a')
console.log(text.indexOf("z"));    // -1 (not found)
console.log(text.indexOf("a", 2)); // 3 (starts searching from index 2)
```

---

### **🔹 `lastIndexOf()` – Last Occurrence**

Finds the **last occurrence** of a substring.

#### **✅ Syntax:**

```js
string.lastIndexOf(searchValue, startIndex)
```

- `searchValue` → The substring to search for.
- `startIndex` _(optional)_ → The position to start searching **backward** from.

#### **✅ Example:**

```js
const text = "JavaScript is amazing!";

console.log(text.lastIndexOf("a"));  // 14 (last 'a')
console.log(text.lastIndexOf("is")); // 11
console.log(text.lastIndexOf("z"));  // -1 (not found)
console.log(text.lastIndexOf("a", 5)); // 3 (searches backward from index 5)
```

---

### **🚀 Key Points**

✔️ **Case-sensitive**  
✔️ **Returns `-1` if the substring is not found**  
✔️ **`indexOf()` searches forward (left to right)**  
✔️ **`lastIndexOf()` searches backward (right to left)**

## **`replace()` Method in JavaScript**

The **`replace()`** method **replaces a substring** or **pattern** inside a string **with another value**. It **returns a new string** without modifying the original one.

---

### **🔹 Syntax**

```js
string.replace(searchValue, newValue)
```

- `searchValue` → The substring or **regular expression** to be replaced.
- `newValue` → The replacement text.

---

### **🔹 Example 1: Replacing a Word (First Occurrence Only)**

```js
const text = "JavaScript is awesome!";

console.log(text.replace("JavaScript", "Python"));  
// Output: "Python is awesome!"
```

✔️ Only replaces **the first occurrence**.

---

### **🔹 Example 2: Using a Regular Expression for Global Replacement**

```js
const text = "I love JavaScript. JavaScript is fun!";

console.log(text.replace(/JavaScript/g, "Python"));
// Output: "I love Python. Python is fun!"
```

✔️ The `/g` flag ensures **all occurrences** are replaced.

---

### **🔹 Example 3: Case-Insensitive Replacement**

```js
const text = "JavaScript is fun. I love JAVASCRIPT.";

console.log(text.replace(/javascript/gi, "Python"));
// Output: "Python is fun. I love Python."
```

✔️ The `/gi` flag makes the search **global (`g`) and case-insensitive (`i`)**.

---

### **🔹 Example 4: Using a Function for Dynamic Replacement**

```js
const text = "I have 3 apples and 5 bananas.";

const result = text.replace(/\d+/g, (match) => match * 2);
console.log(result);
// Output: "I have 6 apples and 10 bananas."
```

✔️ **Replaces numbers dynamically** by multiplying them by 2.

---

### **🚀 Key Points**

✔️ **Returns a new string (does not modify the original)**  
✔️ **Only replaces the first match unless using `/g` (global flag)**  
✔️ **Supports regular expressions for advanced replacements**  
✔️ **Can use a function for dynamic replacements**

## **`trim()` Method in JavaScript**

The **`trim()`** method **removes whitespace** from both **ends** of a string but **does not modify** the original string.

---

### **🔹 Syntax**

```js
string.trim()
```

✔️ Removes **spaces, tabs, and newlines** from the **beginning and end** of the string.

---

### **🔹 Example 1: Removing Extra Spaces**

```js
const text = "   Hello, JavaScript!   ";

console.log(text.trim());  
// Output: "Hello, JavaScript!"
```

---

### **🔹 Example 2: Before and After `trim()`**

```js
const input = "  user123  ";

console.log("Before:", input.length);     // 11
console.log("After:", input.trim().length); // 7
```

✔️ **Great for cleaning user input!**

---

### **🔹 Related Methods**

- **`trimStart()`** → Removes whitespace **only from the beginning**.
- **`trimEnd()`** → Removes whitespace **only from the end**.

```js
const text = "   Hello, World!   ";

console.log(text.trimStart()); // "Hello, World!   "
console.log(text.trimEnd());   // "   Hello, World!"
```

---

### **🚀 Key Points**

✔️ **Removes whitespace from both ends**  
✔️ **Does not change the original string**  
✔️ **Useful for cleaning user input (e.g., form fields)**

## **`charAt()` Method in JavaScript**

The **`charAt()`** method returns the **character at a specified index** in a string.

---

### **🔹 Syntax**

```js
string.charAt(index)
```

- `index` → The position of the character to retrieve.
- If the index is **out of range**, it returns an **empty string (`""`)**.

---

### **🔹 Example 1: Getting a Character at a Specific Index**

```js
const text = "JavaScript";

console.log(text.charAt(0));  // "J"
console.log(text.charAt(4));  // "S"
console.log(text.charAt(10)); // "" (index out of range)
```

---

### **🔹 Example 2: Getting the Last Character**

```js
const text = "Hello";

console.log(text.charAt(text.length - 1));  // "o"
```

✔️ **Useful for extracting the last character dynamically!**

---

### **🔹 Alternative: Using Bracket Notation**

You can also get characters using **bracket notation (`[]`)**:

```js
console.log(text[0]);   // "H"
console.log(text[10]);  // undefined (instead of an empty string)
```

✔️ **Bracket notation is more common in modern JavaScript.**

---

### **🚀 Key Points**

✔️ **Returns a single character from a string**  
✔️ **Returns an empty string (`""`) for out-of-range indexes**  
✔️ **Alternative: Use bracket notation (`[]`) for similar results**

## **`charCodeAt()` and `fromCharCode()` in JavaScript**

These methods deal with **Unicode character codes** in JavaScript strings.

---

### **🔹 `charCodeAt()` – Get Character Code**

The **`charCodeAt()`** method returns the **Unicode value** of a character at a given index.

### **✅ Syntax**

```js
string.charCodeAt(index)
```

- `index` → The position of the character.
- Returns a **number** representing the **UTF-16 code** of the character.

### **✅ Example**

```js
const text = "ABC";

console.log(text.charCodeAt(0));  // 65 (Unicode for 'A')
console.log(text.charCodeAt(1));  // 66 (Unicode for 'B')
console.log(text.charCodeAt(2));  // 67 (Unicode for 'C')
console.log(text.charCodeAt(10)); // NaN (index out of range)
```

---

### **🔹 `fromCharCode()` – Convert Code to Character**

The **`String.fromCharCode()`** method converts **Unicode values** back to characters.

### **✅ Syntax**

```js
String.fromCharCode(code1, code2, ...)
```

- Accepts one or more **Unicode numbers** and returns a **string**.

### **✅ Example**

```js
console.log(String.fromCharCode(65));     // "A"
console.log(String.fromCharCode(66, 67)); // "BC"
console.log(String.fromCharCode(9731));   // "☃" (Snowman symbol)
```

---

### **🚀 Key Points**

✔️ **`charCodeAt()` → Converts character → Unicode**  
✔️ **`fromCharCode()` → Converts Unicode → Character**  
✔️ **UTF-16 encoding is used**  
✔️ **Useful for encoding, decoding, and working with character sets**

## **`concat()` Method in JavaScript**

The **`concat()`** method joins two or more **strings** and returns a **new combined string**. It does **not modify** the original strings.

---

### **🔹 Syntax**

```js
string1.concat(string2, string3, ...)
```

- Accepts one or more **strings** as arguments.
- Returns a **new string** with all the given strings **merged together**.

---

### **🔹 Example 1: Basic Concatenation**

```js
const str1 = "Hello";
const str2 = "World";

console.log(str1.concat(" ", str2, "!"));  
// Output: "Hello World!"
```

---

### **🔹 Example 2: Concatenating Multiple Strings**

```js
const firstName = "Achyuth";
const lastName = "J";

const fullName = firstName.concat(" ", lastName);
console.log(fullName);  // "Achyuth J"
```

---

### **🔹 Alternative: Using `+` or Template Literals**

Instead of `concat()`, you can use **`+` operator** or **template literals (`)**

```js
console.log("Hello".concat(" ", "World"));  // "Hello World"
console.log("Hello" + " " + "World");       // "Hello World"
console.log(`Hello World`);                 // "Hello World"
```

✔️ **Template literals (`) are the modern, preferred way**

---

### **🚀 Key Points**

✔️ **Combines multiple strings**  
✔️ **Does not modify original strings**  
✔️ **Better alternatives: `+` operator or template literals**

## **`split()` Method in JavaScript**

The **`split()`** method splits a string into an **array of substrings** based on a given **separator**.

---

### **🔹 Syntax**

```js
string.split(separator, limit)
```

- **`separator`** → The **character(s) or regex** to split the string by. (Optional, defaults to the entire string)
- **`limit`** → The **maximum number of splits** to return. (Optional)

---

### **🔹 Example 1: Splitting by a Space**

```js
const text = "JavaScript is fun";

console.log(text.split(" "));  
// Output: ["JavaScript", "is", "fun"]
```

---

### **🔹 Example 2: Splitting by a Comma**

```js
const data = "apple,banana,orange";

console.log(data.split(","));  
// Output: ["apple", "banana", "orange"]
```

---

### **🔹 Example 3: Using a Limit**

```js
const text = "one two three four";

console.log(text.split(" ", 2));  
// Output: ["one", "two"]
```

---

### **🔹 Example 4: Splitting Each Character**

```js
const word = "Hello";

console.log(word.split(""));  
// Output: ["H", "e", "l", "l", "o"]
```

---

### **🔹 Example 5: Using a Regular Expression**

```js
const text = "apple123banana456cherry";

console.log(text.split(/\d+/));  
// Output: ["apple", "banana", "cherry"]
```

✔️ **Regex allows advanced splitting (e.g., removing numbers).**

---

### **🚀 Key Points**

✔️ **Splits a string into an array**  
✔️ **Does not modify the original string**  
✔️ **Can use spaces, commas, or regex as separators**  
✔️ **Empty string (`""`) splits into individual characters**

## **`slice()` Method in JavaScript**

The **`slice()`** method extracts a **portion of a string** or **array** and returns it as a **new string/array** **without modifying the original**.

---

### **🔹 Syntax**

```js
string.slice(start, end)
array.slice(start, end)
```

- **`start`** → The **starting index** (inclusive).
- **`end`** _(optional)_ → The **ending index** (exclusive).
- If `end` is **not provided**, it slices **until the end** of the string/array.
- If `start` or `end` is **negative**, it counts from the **end**.

---

### **🔹 `slice()` with Strings**

### **✅ Example 1: Extracting Part of a String**

```js
const text = "JavaScript";

console.log(text.slice(0, 4));   // "Java"
console.log(text.slice(4, 10));  // "Script"
console.log(text.slice(4));      // "Script" (No end index)
```

---

### **✅ Example 2: Using Negative Indexes**

```js
console.log(text.slice(-6, -1)); // "Scrip"
console.log(text.slice(-6));     // "Script"
```

✔️ **Negative values count from the end** (`-1` is the last character).

---

### **🚀 Key Points**

✔️ **Extracts a portion of a string/array**  
✔️ **Does not modify the original string/array**  
✔️ **Supports negative indexes**  
✔️ **End index is exclusive (`end` is not included)**

## **`substr()` vs `substring()` in JavaScript**

Both **`substr()`** and **`substring()`** extract parts of a string, but they work differently in terms of how they define the portion to extract.

---

### **🔹 `substring()` – Extract Using Start & End Index**

### **✅ Syntax**

```js
string.substring(start, end)
```

- **`start`** → The **starting index** (inclusive).
- **`end`** _(optional)_ → The **ending index** (exclusive).
- If `end` is omitted, it extracts **until the end**.
- If `start > end`, JavaScript **swaps** the values automatically.
- **Negative values are treated as `0`**.

### **✅ Example**

```js
const text = "JavaScript";

console.log(text.substring(0, 4));  // "Java"
console.log(text.substring(4, 10)); // "Script"
console.log(text.substring(4));     // "Script" (No end index)
console.log(text.substring(8, 4));  // "Script" (Swaps start & end)
console.log(text.substring(-2, 4)); // "Java" (Negative treated as 0)
```

---

### **🔹 `substr()` – Extract Using Start Index & Length** _(Deprecated)_

### **✅ Syntax**

```js
string.substr(start, length)
```

- **`start`** → The **starting index** (inclusive).
- **`length`** → The **number of characters** to extract.
- If `length` is omitted, it extracts **until the end**.
- If `start` is negative, it **counts from the end**.

### **✅ Example**

```js
console.log(text.substr(0, 4));   // "Java" (Start at index 0, length 4)
console.log(text.substr(4, 6));   // "Script" (Start at index 4, length 6)
console.log(text.substr(4));      // "Script" (No length, extracts till end)
console.log(text.substr(-6, 6));  // "Script" (Negative index counts from end)
```

---

### **🔹 Key Differences**

|Feature|`substring()`|`substr()` _(Deprecated)_|
|---|---|---|
|Second Parameter|End index (exclusive)|Length of substring|
|Swaps `start > end`|✅ Yes|❌ No|
|Supports negative indexes|❌ No (treated as `0`)|✅ Yes (counts from end)|
|Status|Recommended ✅|**Deprecated ❌**|

---

### **🚀 Which One Should You Use?**

✔️ **Use `substring()`**, since `substr()` is **deprecated** in modern JavaScript.  
✔️ **Use `slice()`** if you need **negative index support**.

## **`toString()` vs `valueOf()` 

Both **`toString()`** and **`valueOf()`** are used to retrieve a string representation of a string object, but they work slightly differently.

---

### **🔹 `toString()` – Converts to String**

The **`toString()`** method returns the **string representation** of an object.

### **✅ Syntax**

```js
string.toString()
```

- Works on **String objects and primitives**.
- Returns a **new string** representing the object.

### **✅ Example**

```js
const str = new String("Hello");

console.log(str.toString()); // "Hello"
console.log(typeof str.toString()); // "string"
```

✔️ Converts a **String object** into a **string primitive**.

---

### **🔹 `valueOf()` – Returns Primitive Value**

The **`valueOf()`** method returns the **primitive string value** of a String object.

### **✅ Syntax**

```js
string.valueOf()
```

- Works on **String objects**.
- Returns the **actual primitive string value** stored inside the object.

### **✅ Example**

```js
const strObj = new String("JavaScript");

console.log(strObj.valueOf()); // "JavaScript"
console.log(typeof strObj.valueOf()); // "string"
```

---

### **🔹 Key Differences**

|Feature|`toString()`|`valueOf()`|
|---|---|---|
|Returns|String representation|Primitive string value|
|Works on|Primitives & Objects|Only Objects|
|Common Use|String conversion|Retrieving raw value|
|Explicitly Needed?|Sometimes|Rarely used|

---

### **🚀 Which One Should You Use?**

✔️ **Use `toString()`** when you need to **explicitly convert** something to a string.  
✔️ **Use `valueOf()`** if working with **String objects**, but it's rarely needed (JS converts objects automatically).

Let me know if you need more details! 🚀





# **🚀`forEach()` Method in JavaScript 

The **`forEach()`** method is used to **iterate over an array** and execute a function for each element. Unlike other looping methods, `forEach()` **does not return a new array**; it simply runs the function for each item.

---

## **How `forEach()` Works**

### **🔹 Syntax**

```js
array.forEach(function(element, index, array) {
    // Code to execute
});
```

- `element` → The current item in the array.
- `index` _(optional)_ → The index of the current item.
- `array` _(optional)_ → The entire array being looped over.

---

## **🔹 Example 1: Basic `forEach()` Loop**

```js
const numbers = [1, 2, 3, 4, 5];

numbers.forEach(function(num) {
    console.log(num);
});
```

**Output:**

```
1
2
3
4
5
```

💡 **How it works?**

- Loops through `numbers` and prints each value.

---

## **🔹 Example 2: Using `index` in `forEach()`**

```js
const fruits = ["apple", "banana", "cherry"];

fruits.forEach(function(fruit, index) {
    console.log(`Index ${index}: ${fruit}`);
});
```

**Output:**

```
Index 0: apple
Index 1: banana
Index 2: cherry
```

💡 **Why use `index`?**

- Helps track the position of each element.

---

## **🔹 Example 3: Modifying Objects Inside `forEach()`**

```js
const users = [
    { name: "Achyuth", age: 25 },
    { name: "Yadav", age: 24 },
    { name: "Mahindra", age: 26 }
];

users.forEach(user => user.age++);

console.log(users);
```

**Output:**

```js
[
    { name: "Achyuth", age: 26 },
    { name: "Yadav", age: 25 },
    { name: "Mahindra", age: 27 }
]
```

💡 **Key Point:**

- **`forEach()` can modify objects** inside an array.

---

## **🔹 Example 4: Summing an Array**

```js
let sum = 0;
const numbers = [5, 10, 15];

numbers.forEach(num => sum += num);

console.log(sum);  
// Output: 30
```

💡 **Why use `forEach()` here?**

- Great for cumulative operations like summing values.

---

## **⚠️ Important Limitations of `forEach()`**

### ❌ **Cannot Stop or Break the Loop**

Unlike `for` or `map()`, `forEach()` **always loops through all elements**. You **cannot use `break` or `return`** to stop it.

```js
const numbers = [10, 20, 30, 40];

numbers.forEach(num => {
    if (num === 30) return;  // This does NOT stop the loop!
    console.log(num);
});
```

**Output:**

```
10
20
40
```

💡 **Alternative?** Use `some()` or `every()` if you need to stop early.

### ❌ **Does Not Return a New Array**

```js
const arr = [1, 2, 3];
const newArr = arr.forEach(num => num * 2);
console.log(newArr);  
// Output: undefined
```

💡 **Alternative?** Use `map()` if you need a new array.

---

## **✅ When to Use `forEach()`**

✔️ When you need to **iterate through an array** and perform an action.  
✔️ When modifying elements **inside an array** (like updating object properties).  
✔️ When logging or debugging array elements.

❌ **Don't use `forEach()` when you need a new array** → Use `map()` instead.  
❌ **Don't use `forEach()` when you need to stop the loop early** → Use `some()` or `every()`.

---

## **🚀 Final Summary**

|Feature|`forEach()`|
|---|---|
|**Modifies original array?**|❌ No (but can modify objects inside)|
|**Returns new array?**|❌ No|
|**Can be stopped with `break`?**|❌ No|
|**Best Use Case**|Running a function for each item|


# **🚀`map()` Method in JavaScript 

The **`map()`** method is used to **transform an array** by applying a function to each element, and it **returns a new array** with the modified values. Unlike `forEach()`, **`map()` does not modify the original array**.

---

## **🔹 Syntax**

```js
const newArray = array.map(function(element, index, array) {
    // return modified element
});
```

- `element` → The current item being processed.
- `index` _(optional)_ → The index of the current element.
- `array` _(optional)_ → The entire array being processed.

---

## **🔹 Example 1: Doubling Numbers in an Array**

```js
const numbers = [1, 2, 3, 4, 5];

const doubled = numbers.map(num => num * 2);

console.log(doubled);
// Output: [2, 4, 6, 8, 10]
```

💡 **Why use `map()` here?**

- It **returns a new array** without modifying `numbers`.

---

## **🔹 Example 2: Extracting Specific Object Properties**

```js
const users = [
    { name: "Achyuth", age: 25 },
    { name: "Yadav", age: 24 },
    { name: "Mahindra", age: 26 }
];

const names = users.map(user => user.name);

console.log(names);
// Output: ["Achyuth", "Yadav", "Mahindra"]
```

💡 **Why use `map()` here?**

- It **creates an array** containing only names from `users`.

---

## **🔹 Example 3: Converting an Array of Strings to Uppercase**

```js
const words = ["hello", "world", "javascript"];

const upperCaseWords = words.map(word => word.toUpperCase());

console.log(upperCaseWords);
// Output: ["HELLO", "WORLD", "JAVASCRIPT"]
```

💡 **Why use `map()` here?**

- It **transforms each string** into uppercase.

---

## **🔹 Example 4: Adding a New Property to Each Object**

```js
const students = [
    { name: "John", marks: 85 },
    { name: "Sara", marks: 90 },
    { name: "David", marks: 78 }
];

const updatedStudents = students.map(student => ({
    ...student,  // Spread existing properties
    passed: student.marks >= 80  // New property
}));

console.log(updatedStudents);
```

**Output:**

```js
[
    { name: "John", marks: 85, passed: true },
    { name: "Sara", marks: 90, passed: true },
    { name: "David", marks: 78, passed: false }
]
```

💡 **Why use `map()` here?**

- It **creates a new array of objects** with an added `passed` property.

---

## **🔹 Example 5: Modifying Elements Based on Index**

```js
const numbers = [10, 20, 30];

const multipliedByIndex = numbers.map((num, index) => num * index);

console.log(multipliedByIndex);
// Output: [0, 20, 60]  (10*0, 20*1, 30*2)
```

💡 **Why use `map()` here?**

- The **index is used** to modify elements.

---

## **🔹 Difference Between `map()` and `forEach()`**

|Feature|`map()`|`forEach()`|
|---|---|---|
|**Returns a new array?**|✅ Yes|❌ No|
|**Modifies the original array?**|❌ No|❌ No|
|**Used for transformations?**|✅ Yes|❌ No|
|**Used for performing actions (logging, updating variables)?**|❌ No|✅ Yes|

---

## **✅ When to Use `map()`**

✔️ When you **need a new array** with transformed values.  
✔️ When you **extract specific properties** from objects.  
✔️ When you **modify objects while keeping the original array unchanged**.

❌ **Don't use `map()`** if you only need to **iterate** (use `forEach()` instead).

---

## **🚀 Final Summary**

- `map()` **creates a new array** based on the original.
- **Original array remains unchanged**.
- Used for **transforming** data (numbers, objects, strings, etc.).
- **Always returns a new array**.


 
# **🚀`filter()` Method in JavaScript – In Depth Explanation

The **`filter()`** method is a **higher-order function** used to create a **new array** containing only the elements that satisfy a specified condition. It does **not modify the original array**.

✅ **Returns a new array** with matching elements.  
❌ **If no elements match**, it returns an **empty array** (`[]`).

---

### **🔹 How `filter()` Works Internally**

1. `filter()` iterates over each element in the array.
2. It applies the provided callback function to each element.
3. If the callback function **returns `true`**, the element is added to the new array.
4. If the callback function **returns `false`**, the element is skipped.
5. Once all elements are checked, `filter()` returns the **new array** with only the matching elements.

---

### **🔹 Syntax**

```js
array.filter((element, index, array) => condition);
```

- `element` – The current element being processed.
- `index` _(optional)_ – The index of the current element.
- `array` _(optional)_ – The full array being processed.

---

### **1. Basic Example – Filtering Even Numbers**

```js
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

const evenNumbers = numbers.filter(num => num % 2 === 0);
console.log(evenNumbers); // Output: [2, 4, 6, 8, 10]
```

💡 **How it works:**

- `num % 2 === 0` is checked for each number.
- If `true`, the number is included in the new array.
- If `false`, the number is skipped.

---

### **2. Filtering Objects – Getting Adults**

```js
const users = [
    { name: "Achyuth", age: 25 },
    { name: "Yadav", age: 17 },
    { name: "Mahindra", age: 22 },
    { name: "Raj", age: 15 }
];

const adults = users.filter(user => user.age >= 18);
console.log(adults);
/* Output:
[
    { name: "Achyuth", age: 25 },
    { name: "Mahindra", age: 22 }
]
*/
```

💡 **How it works:**

- `user.age >= 18` is checked for each object.
- If `true`, the object is included.
- If `false`, the object is skipped.

---

### **3. Filtering Strings – Words That Start With "A"**

```js
const words = ["apple", "banana", "cherry", "avocado", "blueberry"];

const aWords = words.filter(word => word.startsWith("a"));
console.log(aWords); // Output: ["apple", "avocado"]
```

💡 **How it works:**

- `.startsWith("a")` checks if a word starts with `"a"`.
- If `true`, it is included in the new array.

---

### **4. Removing Falsy Values (Truthy Filter)**

```js
const mixedArray = [0, 1, false, 2, "", 3, null, "hello", undefined, NaN];

const truthyValues = mixedArray.filter(Boolean);
console.log(truthyValues); // Output: [1, 2, 3, "hello"]
```

💡 **How it works:**

- `Boolean(value)` converts values to `true` (truthy) or `false` (falsy).
- Falsy values (`false`, `0`, `""`, `null`, `undefined`, `NaN`) are **removed**.

---

### **5. Filtering with Index Parameter**

You can also use the **index** inside the callback function.

```js
const numbers = [10, 20, 30, 40, 50];

const filteredNumbers = numbers.filter((num, index) => index % 2 === 0);
console.log(filteredNumbers); // Output: [10, 30, 50] (Only even index values)
```

💡 **How it works:**

- The filter keeps numbers where `index % 2 === 0`, meaning only elements at even indexes are included.

---

### **6. Filtering an Array of Objects Based on Multiple Conditions**

```js
const products = [
    { name: "Laptop", price: 1200, inStock: true },
    { name: "Phone", price: 800, inStock: false },
    { name: "Tablet", price: 600, inStock: true },
    { name: "Monitor", price: 300, inStock: true }
];

const affordableAndInStock = products.filter(product => product.price < 1000 && product.inStock);
console.log(affordableAndInStock);
/* Output:
[
    { name: "Tablet", price: 600, inStock: true },
    { name: "Monitor", price: 300, inStock: true }
]
*/
```

💡 **How it works:**

- Only products with `price < 1000` and `inStock === true` are included.

---

### **🔹 Key Differences: `filter()` vs. `find()` vs. `findIndex()`**

|Method|Purpose|Returns|When No Match Found|
|---|---|---|---|
|`filter()`|Finds **all** matching elements|A **new array** with matches|`[]` (empty array)|
|`find()`|Finds **only the first** matching element|The element itself|`undefined`|
|`findIndex()`|Finds the **index** of the first matching element|Index number|`-1`|

---

### **🔹 When to Use `filter()`**

✔ When you need **multiple matches**.  
✔ When you want to **remove unwanted elements**.  
✔ When working with **arrays of objects** (filtering based on properties).

---

### **🔹 Performance Considerations**

- **`filter()` runs for all elements**, even if the first few satisfy the condition.
- **If you only need the first match**, use `find()` instead for better performance.

---

### **Conclusion**

The **`filter()`** method is powerful for working with arrays when you need to find multiple elements that match a condition. It is especially useful for **searching, removing unwanted values, and filtering objects based on properties**.

# 🚀**The `this` Keyword in JavaScript Objects

The **`this`** keyword in JavaScript refers to the **object that is executing the current function**. Its value depends on **how and where** it is used.

---

## **🔹 How `this` Works in Objects**

In an object, `this` refers to the **current object**.

### **Example: Using `this` Inside an Object**

```js
const person = {
    name: "Achyuth",
    age: 25,
    greet: function() {
        console.log(`Hello, my name is ${this.name}`);
    }
};

person.greet();
// Output: "Hello, my name is Achyuth"
```

💡 **How it works?**

- `this.name` refers to the **`name` property of the `person` object`**.

---

## **🔹 `this` in a Nested Object**

```js
const user = {
    name: "Yadav",
    details: {
        age: 24,
        showAge: function() {
            console.log(this.age);
        }
    }
};

user.details.showAge();
// Output: 24
```

💡 **Why?**

- `this` refers to the `details` object because `showAge` is inside it.

---

## **🔹 `this` in a Function Inside an Object**

If you use `this` inside a **regular function** inside an object, it **loses** reference to the object.

### **Example: `this` in a Regular Function**

```js
const person = {
    name: "Mahindra",
    greet: function() {
        function inner() {
            console.log(this.name);
        }
        inner();
    }
};

person.greet();
// Output: undefined (or error in strict mode)
```

💡 **Why?**

- `this` in `inner()` refers to **`window` (or `undefined` in strict mode)**, not `person`.

✅ **Solution:** Use an Arrow Function

```js
const person = {
    name: "Mahindra",
    greet: function() {
        const inner = () => {
            console.log(this.name);
        };
        inner();
    }
};

person.greet();
// Output: "Mahindra"
```

💡 **Why?**

- Arrow functions **do not have their own `this`**; they inherit `this` from the surrounding scope.

---

## **🔹 `this` in an Object Method Called With `setTimeout()`**

```js
const user = {
    name: "Achyuth",
    show: function() {
        setTimeout(function() {
            console.log(this.name);
        }, 1000);
    }
};

user.show();
// Output: undefined (or error in strict mode)
```

💡 **Why?**

- The `this` inside `setTimeout()` refers to `window`, not `user`.

✅ **Solution:** Use an Arrow Function

```js
const user = {
    name: "Achyuth",
    show: function() {
        setTimeout(() => {
            console.log(this.name);
        }, 1000);
    }
};

user.show();
// Output: "Achyuth"
```

💡 **Arrow functions inherit `this` from their surrounding scope (`user`).**

---

## **🔹 `this` with `call()`, `apply()`, and `bind()`**

You can explicitly set the value of `this` using these methods.

### **1️⃣ `call()` – Call a Function with a Specific `this`**

```js
const user1 = { name: "Yadav" };
const user2 = { name: "Mahindra" };

function greet() {
    console.log(`Hello, ${this.name}`);
}

greet.call(user1);  // Output: "Hello, Yadav"
greet.call(user2);  // Output: "Hello, Mahindra"
```

### **2️⃣ `apply()` – Like `call()`, but Passes Arguments as an Array**

```js
function introduce(city, country) {
    console.log(`${this.name} is from ${city}, ${country}`);
}

introduce.apply(user1, ["Kollam", "India"]);
// Output: "Yadav is from Kollam, India"
```

### **3️⃣ `bind()` – Creates a New Function with a Fixed `this`**

```js
const sayHello = greet.bind(user1);
sayHello(); 
// Output: "Hello, Yadav"
```

💡 **`bind()` does not execute the function immediately; it returns a new function.**

---

## **🔹 Summary of `this` in Objects**

|Scenario|Value of `this`|
|---|---|
|**Inside an object method**|The object itself|
|**Inside a regular function**|`window` (or `undefined` in strict mode)|
|**Inside an arrow function**|Inherits from surrounding scope|
|**Inside `setTimeout()`**|Defaults to `window`, unless using an arrow function|
|**With `call()`, `apply()`, `bind()`**|Explicitly set to a specific object|

---

## **🚀 Final Takeaways**

✔️ **Use arrow functions when you want to inherit `this` from the parent scope.**  
✔️ **Use `call()`, `apply()`, or `bind()` to explicitly set `this`.**  
✔️ **Inside object methods, `this` refers to the object.**



# 🚀Difference between regular function and arrow function


## ✅ **1️⃣ Syntax difference**

### Traditional function:

```js
function add(a, b) {
  return a + b;
}
```

### Arrow function:

```js
const add = (a, b) => a + b;
```

---

## ✅ **2️⃣ `this` binding**

- **Traditional functions** have their **own `this` context**, which changes depending on **how the function is called** (object method, normal function, event handler, etc.).
    
- **Arrow functions do NOT have their own `this`.**  
    They **lexically bind `this` from their surrounding scope.**
    

**Example:**

```js
const obj = {
  name: "Achyuth",
  showNameTraditional: function() {
    console.log(this.name); // "Achyuth"
  },
  showNameArrow: () => {
    console.log(this.name); // undefined (takes `this` from outside, likely `window` in browsers)
  }
};
obj.showNameTraditional();
obj.showNameArrow();
```

---

## ✅ **3️⃣ `arguments` object**

- **Traditional functions** have access to the **`arguments` object**, which holds all arguments passed to the function.
    
- **Arrow functions do NOT have their own `arguments`.**  
    They inherit `arguments` from their outer scope (if any), or `arguments` will be undefined.
    

**Example:**

```js
function showArgs() {
  console.log(arguments);
}
showArgs(1, 2, 3); // [1, 2, 3]

const showArgsArrow = () => {
  console.log(arguments);
};
showArgsArrow(1, 2, 3); // ReferenceError: arguments is not defined
```

---

## ✅ **4️⃣ Constructor usage**

- **Traditional functions** can be used as **constructors** with `new` to create instances:
    

```js
function Person(name) {
  this.name = name;
}
const p = new Person("Don");
```

- **Arrow functions CANNOT be used as constructors.**  
    Using `new` with an arrow function will throw:
    
    ```
    TypeError: Arrow functions cannot be used as constructors
    ```
    

---

## ✅ **5️⃣ Methods in objects**

- Arrow functions should **NOT** be used as methods in objects if you need correct `this` binding.
    
- Traditional functions are **better suited** for object methods.
    

---

## ✅ **Summary Table**

|Aspect|Traditional Function|Arrow Function|
|---|---|---|
|**Syntax**|`function fname() {}`|`const fname = () => {}`|
|**`this`**|Own dynamic `this`|Lexical `this`|
|**`arguments`**|Available|Not available|
|**Constructor**|Can use `new`|Cannot use `new`|
|**Best for methods**|Yes|No (if needs `this`)|

---

## ⚡ Practical Rule:

✅ Use **arrow functions for callbacks, simple functional operations, and when you need lexical `this`.**  
✅ Use **traditional functions for object methods, constructors, and when you need dynamic `this` or `arguments`.**

---

If you want, I can also prepare **practice examples showing `this` differences visually** for deeper clarity. Let me know!