
# What is Bubble Sort?

**Bubble Sort** is a simple sorting algorithm that compares **adjacent elements** and **swaps them** if they are in the wrong order. This process is repeated until the list is sorted.

Just like bubbles rise to the top in water, **the largest elements "bubble up"** to the end of the array in each pass — hence the name **Bubble Sort**.

---

### 🧠 How Bubble Sort Works (Step-by-Step)

Let’s take an example array:  
`[5, 3, 8, 4, 2]`

We’ll sort it in **ascending order**.

#### **Pass 1**:

- Compare 5 and 3 → swap → `[3, 5, 8, 4, 2]`
    
- Compare 5 and 8 → no swap
    
- Compare 8 and 4 → swap → `[3, 5, 4, 8, 2]`
    
- Compare 8 and 2 → swap → `[3, 5, 4, 2, 8]` ← largest element 8 is now at the end
    

#### **Pass 2**:

- Compare 3 and 5 → no swap
    
- Compare 5 and 4 → swap → `[3, 4, 5, 2, 8]`
    
- Compare 5 and 2 → swap → `[3, 4, 2, 5, 8]`
    
- (No need to touch the last element, it’s already sorted)
    

Keep repeating until no swaps are needed. That’s when the array is sorted.

---

### 📜 Bubble Sort Pseudocode

```javascript
function bubbleSort(arr) {
    let n = arr.length;
    for (let i = 0; i < n - 1; i++) {
        let swapped = false;
        for (let j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                // Swap
                [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
                swapped = true;
            }
        }
        if (!swapped) break; // Optimization: Stop early if no swaps
    }
    return arr;
}
```

---

### 🧮 Time Complexity

|Case|Time Complexity|
|---|---|
|Best (already sorted)|`O(n)` with optimization|
|Average|`O(n²)`|
|Worst|`O(n²)`|

🧠 Best case works in O(n) if we add that `swapped` flag to detect if a pass made no changes.

---

### 🪙 Space Complexity

- `O(1)` — It sorts **in-place**, no extra memory required.
    

---

### ✅ Merits of Bubble Sort

1. **Simple & easy to implement** – great for beginners learning sorting.
    
2. **Stable sort** – maintains the relative order of equal elements.
    
3. **In-place** – doesn’t require extra memory.
    
4. **Early stopping** – if the array becomes sorted early, it can exit fast.
    

---

### ❌ Demerits of Bubble Sort

1. **Inefficient on large datasets** – has `O(n²)` time complexity.
    
2. **Too many swaps and comparisons** – even for nearly sorted arrays (without optimization).
    
3. **Not used in production** – better algorithms like Merge Sort or Quick Sort are used.
    

---

### 💼 Applications of Bubble Sort

Even though it's not practical for large datasets, it’s still useful in:

- **Educational purposes** – to teach the concept of sorting and algorithm design.
    
- **Small datasets** – where performance isn't a concern.
    
- **Partially sorted data** – with early termination optimization, it can perform decently.
    
- **Hardware-constrained systems** – where simplicity and low memory usage are more important than speed.
    

---

### 🧠 TL;DR

> **Bubble Sort** = Swap neighbors until sorted. Easy to understand, slow to run.

---




# What is Insertion Sort?

**Insertion Sort** is one of the simplest and most intuitive sorting algorithms. It mimics the way humans often sort items—like **sorting a hand of playing cards**.

---

### 🃏 Real-Life Analogy – Sorting Playing Cards

Imagine you're holding cards in your hand. You start with one card, and as each new card comes in:

- You **compare** it with the cards in your hand from **right to left**.
    
- You **shift** the larger cards one position to the right.
    
- You then **insert** the new card into the right place.
    

This is **exactly** what insertion sort does, but with numbers in an array.

---

## 🛠️ Step-by-Step Working of Insertion Sort

Let’s break it down using an example:

### Array:

`[5, 8, 12, 4, 1, 9, 30]`

1. **Start from index 1** (element `8`).
    
2. Compare it with the previous element (`5`). Since `5 < 8`, do nothing.
    
3. Next, take `12`. Compare with `8`, no change.
    
4. Now take `4`:
    
    - `4 < 12` → shift `12`
        
    - `4 < 8` → shift `8`
        
    - `4 < 5` → shift `5`
        
    - Place `4` at index 0 → `[4, 5, 8, 12, 1, 9, 30]`
        
5. Next, take `1`:
    
    - `1 < 12`, `1 < 8`, `1 < 5`, `1 < 4`
        
    - Place `1` at index 0 → `[1, 4, 5, 8, 12, 9, 30]`
        
6. Take `9`:
    
    - `9 < 12` → shift `12`
        
    - Place `9` → `[1, 4, 5, 8, 9, 12, 30]`
        
7. `30` is already greater than all, stays in place.
    

---

## 📦 Use Cases of Insertion Sort

### ✔️ 1. Small Datasets

For small arrays (say <20 elements), insertion sort is fast and efficient compared to complex algorithms which need extra memory or overhead.

### ✔️ 2. Nearly Sorted Data

If the array is already **almost sorted**, insertion sort performs very fast — even **linear time (O(n))**.

### ✔️ 3. Online Sorting

It can sort data **as it comes** (e.g., real-time leaderboards). Other algorithms usually need the whole dataset before starting.

### ✔️ 4. In Embedded Systems

Where memory is tight and operations must be fast and simple, this algorithm is ideal because:

- It uses **no extra space**
    
- It involves simple logic
    

---

## 🔄 How It Differs from Other Sorts

|Feature|Insertion Sort|Other Sorts|
|---|---|---|
|Best for small/near-sorted?|✅ Yes|❌ Mostly No|
|Space used|O(1) (in-place)|Merge sort: O(n), others vary|
|Is it stable?|✅ Yes|Quick Sort: ❌ No|
|Speed on large data|❌ Slow (O(n²))|Merge/Quick Sort: ✅ Fast (O(n log n))|

---

## 📊 Complexity Analysis

### 🕒 Time Complexity:

|Case|Explanation|Time|
|---|---|---|
|Best Case|Already sorted → only 1 comparison per item|O(n)|
|Average Case|Elements randomly ordered|O(n²)|
|Worst Case|Reverse sorted → compare & shift all for each element|O(n²)|

### 🧠 Why O(n²) in worst case?

Imagine each new element has to go back to the start and push every other element forward. That’s n comparisons for each of the n elements.

---

### 💾 Space Complexity:

- **O(1)** → Because it sorts in-place (doesn’t need extra arrays or data structures)
    

---

### 💡 Adaptive?

- **YES**: If the input is already sorted or almost sorted, Insertion Sort becomes very efficient.
    

---

## ✅ Stability

Insertion sort is a **stable sorting algorithm**.

That means if you have two elements with the same value, their **relative order stays the same** after sorting.

Why is this important?  
In real-world scenarios like sorting by name and then age, stability helps preserve the primary order.

---

## ⚙️ Real-World Applications

|Application|Why Insertion Sort?|
|---|---|
|Card games (e.g., sorting your hand)|Mimics human behavior in sorting|
|Online systems (live data, one by one)|Handles data as it arrives, no waiting|
|Leaderboards (live games)|Sort new scores instantly in order|
|Small real-time tasks in hardware|Low memory, fast, reliable|
|Compiler optimization (instruction reordering)|Efficient for small instruction blocks|

---

## 🧪 Pseudocode

```plaintext
for i = 1 to length(array) - 1
    key = array[i]
    j = i - 1
    while j >= 0 and array[j] > key
        array[j + 1] = array[j]   // shift
        j = j - 1
    array[j + 1] = key            // insert
```

---

## 🧵 Summary

|Feature|Value|
|---|---|
|Type|Comparison-based, In-place|
|Stability|✅ Stable|
|Time (Best)|O(n)|
|Time (Average/Worst)|O(n²)|
|Space|O(1)|
|Adaptive|✅ Yes|
|Real Uses|Cards, live data, embedded|

---

### 🚀 TL;DR

- Great for **small or nearly sorted arrays**
    
- Simple to code and understand
    
- Performs poorly on large, unsorted data (O(n²))
    
- **In-place**, **adaptive**, and **stable**
    

---


# What is **Selection Sort**?

**Selection Sort** is a simple comparison-based sorting algorithm. It works by **repeatedly selecting the smallest (or largest) element** from the unsorted portion of the array and swapping it with the first unsorted element.

It’s like picking the smallest player from the rest of your cricket team and putting them in the opening lineup one by one.

---
![[Pasted image 20250626233855.png]]
![[Pasted image 20250626233938.png]]
## 🔧 How Selection Sort Works – Step by Step

Let’s say we have this array:

```js
[6, 3, 8, 5, 2]
```

### Steps:

1. **Find the minimum element** in the array. That’s `2`.
    
2. **Swap it with the first element** → `[2, 3, 8, 5, 6]`
    
3. Now, find the minimum from index `1` to `4`, which is `3` → already in place
    
4. Find the min from `2` to `4`, which is `5`, swap with `8` → `[2, 3, 5, 8, 6]`
    
5. Continue this till the array is sorted → `[2, 3, 5, 6, 8]`
    

So in every step, you're _selecting_ the smallest one and fixing it at the correct position. That’s why it's called **Selection Sort**.

---

## 🧮 Time Complexity Analysis

|Case|Time Complexity|
|---|---|
|Best Case|O(n²)|
|Average Case|O(n²)|
|Worst Case|O(n²)|

> Why?  
> For every position, you search the remaining elements to find the min →  
> That’s `n + (n-1) + (n-2) + ... + 1 = O(n²)`

### 🧠 Space Complexity

- **O(1)** — It's an **in-place algorithm**, meaning it doesn't use any extra memory.
    

---

## ✅ Is Selection Sort Stable?

> ❌ No.  
> It is **not stable** by default. Stability means the relative order of equal elements is preserved.

But with modifications, you _can_ make it stable.

---

## 🧰 Use Cases & Practical Applications

### ❌ Not used in real-world large-scale applications.

Selection Sort is mostly used for:

- **Learning purposes**: It’s taught as an introductory sorting algorithm in CS courses.
    
- **When memory is very limited**: Because of its constant space usage.
    
- **Small datasets**: Where the overhead of more complex algorithms like quicksort isn't worth it.
    
- **Embedded systems**: Sometimes used in low-resource environments.
    

### Example:

Sorting a list of 10 students based on roll numbers in a microcontroller-based system where memory is tight.

---

## 🚫 When NOT to Use Selection Sort

- When performance matters (i.e., big datasets)
    
- If you want a stable sort (use Insertion Sort or Merge Sort instead)
    

---

## 🧪 Code (JS Example)

```javascript
function selectionSort(arr) {
    let n = arr.length;

    for (let i = 0; i < n - 1; i++) {
        let minIndex = i;

        for (let j = i + 1; j < n; j++) {
            if (arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }

        // Swap the found minimum with the first unsorted element
        [arr[i], arr[minIndex]] = [arr[minIndex], arr[i]];
    }

    return arr;
}

console.log(selectionSort([6, 3, 8, 5, 2])); // Output: [2, 3, 5, 6, 8]
```

---

## 🔚 Final Thoughts

**Selection Sort = Simple but slow**.  
✅ Good for understanding how sorting works.  
⚠️ Avoid for large or time-critical tasks.


# **What is Merge Sort?**

**Merge Sort** is a **divide-and-conquer** sorting algorithm that breaks the array into smaller subarrays, sorts them, and then merges them back together in a sorted manner.

- there are two types i) recursive ii) in place 

👉 It was invented by **John von Neumann in 1945**.

---

## ⚙️ **How Merge Sort Works (Step-by-Step)**

1. **Divide**: Recursively divide the array into two halves until each subarray has **one or zero elements** (which are inherently sorted).
    
2. **Conquer (Sort)**: Sort the two halves.
    
3. **Merge**: Merge the two sorted halves into a single sorted array.
    

### 👇 Example:

Given array: `[38, 27, 43, 3, 9, 82, 10]`

- Split until single elements: `[38] [27] [43] [3] [9] [82] [10]`
    
- Merge & sort step by step:  
    `[27,38] [3,43] [9,82] [10]`  
    `[3,27,38,43] [9,10,82]`  
    `→ [3,9,10,27,38,43,82]`
    

---

## 📊 **Time Complexity Analysis**

|Case|Time Complexity|Explanation|
|---|---|---|
|Best Case|O(n log n)|Even when already sorted, it divides and merges|
|Average Case|O(n log n)|Consistent regardless of input|
|Worst Case|O(n log n)|Always splits and merges|
|Space|O(n)|Needs extra space to merge arrays|

✅ **Stable Sort**: Yes  
✅ **Deterministic**: Yes

---

## 🔍 **Why O(n log n)?**

- You split the array in half each time → log₂(n) levels.
    
- At each level, merging all elements takes O(n).
    
- So, total = **O(n) × O(log n) = O(n log n)**.
    

---

## 🟢 **Advantages of Merge Sort**

1. ✅ **Consistent O(n log n)** time in all cases.
    
2. ✅ **Stable sort** – maintains relative order of equal elements.
    
3. ✅ **Works well with linked lists**, as merging is easy in them.
    
4. ✅ **Efficient for large data** that doesn’t fit in RAM (external sorting).
    
5. ✅ **Predictable performance** – unlike quicksort which can degrade.
    

---

## 🔴 **Disadvantages of Merge Sort**

1. ❌ **Uses O(n) extra space**, not in-place.
    
2. ❌ **Slower for small arrays** than simpler algorithms like Insertion Sort.
    
3. ❌ **More overhead** in recursive calls (stack usage).
    
4. ❌ **Not cache-friendly**, due to non-local access patterns in merging.
    

---

## 🧠 **Use Cases of Merge Sort**

|Use Case|Why Merge Sort?|
|---|---|
|📀 **External Sorting (large files)**|Merge Sort works well with disk-based data.|
|🧵 **Linked Lists**|No extra space needed for merge step.|
|💼 **Stable Sorting Requirement**|Keeps equal elements in original order.|
|🏢 **Parallel Processing**|Divide and merge steps can be done in parallel.|
|📊 **Data Analysis Tools**|Handles massive datasets predictably.|

---

## 💡 Merge Sort vs Other Algorithms

|Feature|Merge Sort|Quick Sort|Insertion Sort|
|---|---|---|---|
|Time (Best/Worst)|O(n log n)|O(n²) worst|O(n²) worst|
|Space|O(n)|O(log n)|O(1)|
|Stable|Yes|No|Yes|
|In-place|No|Yes|Yes|
|Linked Lists|Good|Bad|Good|

---

## 💻 JavaScript Sample Code

```js
function mergeSort(arr) {
  if (arr.length <= 1) return arr;

  let mid = Math.floor(arr.length / 2);
  let left = mergeSort(arr.slice(0, mid));
  let right = mergeSort(arr.slice(mid));

  return merge(left, right);
}

function merge(left, right) {
  let result = [], i = 0, j = 0;

  while (i < left.length && j < right.length) {
    if (left[i] <= right[j]) result.push(left[i++]);
    else result.push(right[j++]);
  }

  return result.concat(left.slice(i)).concat(right.slice(j));
}
```

---

## 🧠 Summary

- **Merge Sort** is great for **large, stable sorting tasks**, especially with **linked lists** or **external data**.
    
- It’s reliable, consistent, and easy to parallelize.
    
- However, it’s not space-efficient, and overkill for small datasets.
    



# What is **Quick Sort**?

**Quick Sort** is a **divide and conquer** algorithm used to sort elements in an array or list. It picks a **pivot element** and partitions the array such that:

- All elements **less than the pivot** go to its **left**
    
- All elements **greater than the pivot** go to its **right**
    

Then it recursively applies the same process to the left and right parts.

---
![[Pasted image 20250626220158.png]]

![[Pasted image 20250626220741.png]]

![[Pasted image 20250626221627.png]]
### ⚙️ How Quick Sort Works (Step-by-Step):

#### 1. **Choose a Pivot**

- Random, first, last, or median element — the choice affects performance.
    

#### 2. **Partition the Array**

- Rearrange elements so that:
    
    - Elements `< pivot` go to the left
        
    - Elements `> pivot` go to the right
        

#### 3. **Recursively Apply**

- Apply the same logic to left and right parts of the pivot.
    

---

### 🔢 Example:

```javascript
let arr = [8, 4, 7, 3, 10];

QuickSort(arr):
- Choose pivot = 8
- Partition:
   Left: [4, 7, 3]
   Pivot: 8
   Right: [10]

Recursively sort Left and Right:
- Left = [3, 4, 7] → sorted
- Right = [10] → already sorted

Final result: [3, 4, 7, 8, 10]
```

---

## 🧠 Real-World Applications

1. **Systems Programming**
    
    - Used in C’s standard library (`qsort()`), Python's internal sort (Timsort uses Quick Sort under the hood for small arrays)
        
2. **Databases**
    
    - Efficient for in-memory sorting of rows and indexing.
        
3. **Embedded Systems**
    
    - Good choice where memory is limited due to in-place sorting.
        
4. **Gaming**
    
    - Sorting scores, rendering objects by depth, etc.
        
5. **Search Optimization**
    
    - Pre-sorting elements helps improve binary search performance.
        

---

## ✅ Advantages of Quick Sort

|Feature|Benefit|
|---|---|
|🧠 **Efficient on average**|O(n log n) time is fast compared to Bubble or Insertion|
|🧠 **In-place**|Doesn’t use much extra memory|
|🔁 **Tail Recursion**|Optimizations can avoid deep recursion|
|📉 **Low overhead**|Faster in practice due to tight loop and fewer comparisons|

---

## ❌ Disadvantages of Quick Sort

|Issue|Explanation|
|---|---|
|😬 **Worst-case time O(n²)**|Happens when pivot is poorly chosen (e.g., smallest/largest every time in sorted array)|
|💣 **Recursive stack overflow**|Deep recursion can crash for large arrays (unless optimized)|
|⚠️ **Unstable Sort**|It doesn’t preserve the original order of equal elements (unlike Merge Sort)|
|🧩 **Not good for small arrays**|Insertion Sort may perform better on small datasets|

---

## ⏱️ Time & Space Complexity

|Case|Time Complexity|
|---|---|
|🔵 **Best Case**|O(n log n) → perfectly balanced partitions|
|🟡 **Average Case**|O(n log n) → random pivots|
|🔴 **Worst Case**|O(n²) → sorted array with poor pivot|

### 📦 Space Complexity:

- **O(log n)** on average (due to recursion stack)
    
- Still **in-place**: no extra array is created
    

---

## 🆚 Quick Sort vs Merge Sort

| Feature      | Quick Sort          | Merge Sort          |
| ------------ | ------------------- | ------------------- |
| Time (avg)   | O(n log n)          | O(n log n)          |
| Space        | O(log n) (in-place) | O(n) (extra memory) |
| Stability    | ❌ Not Stable        | ✅ Stable            |
| Speed (Real) | ⚡ Usually faster    | 🐢 Slightly slower  |

---

## 📌 Summary (TL;DR):

- **Quick Sort** is a fast, in-place sorting algorithm using divide and conquer.
    
- Best for large datasets when memory is a concern.
    
- Avoids extra memory usage.
    
- Has bad worst-case time, but can be optimized with random pivots or hybrid strategies.
    
- Used in real systems due to its speed and efficiency.
    



# Quick Sort Time Complexity

### ✅ Best Case: **O(n log n)**

### ⚖️ Average Case: **O(n log n)**

### ❌ Worst Case: **O(n²)**

---
![[Pasted image 20250626224606.png]]
### ⚙️ Why is Best and Average Case **O(n log n)**?

Quick Sort follows the **divide and conquer** approach:

1. **Divide step**: Partition the array using a pivot.
    
2. **Conquer step**: Recursively sort left and right subarrays.
    

If the pivot divides the array into two roughly equal halves each time, this is what happens:

- Total levels of recursion ≈ **log n** (binary tree style)
    
- At each level, the total work (comparisons and swaps) across the whole array is **O(n)**
    

📊 So:  
`O(n)` (work per level) × `O(log n)` (levels) = **O(n log n)**

---

### ❌ Worst Case: **O(n²)** – When & Why?

This happens when the pivot doesn't divide the array well.

#### 👇 Typical worst cases:

- Array is already sorted or reverse-sorted
    
- Pivot is always the smallest or largest element
    

#### What goes wrong?

- Each partition creates one **big chunk** (n−1) and one **tiny chunk** (0)
    
- Recursion depth becomes `n` instead of `log n`
    
- So total comparisons become:
    

📉 `O(n)` (1st level) + `O(n-1)` + `O(n-2)` + ... + `O(1)` = **O(n²)**

---

### ⏱️ Space Complexity:

- Quick Sort is **in-place**, so extra memory ≈ **O(log n)** (for recursion stack, not for extra arrays)
    
- Worst case space: **O(n)** if recursion goes too deep (unbalanced tree)
    

---

### 📈 Quick Summary Table:

|Case|Time Complexity|When It Happens|
|---|---|---|
|Best Case|O(n log n)|Pivot divides array into equal halves|
|Average Case|O(n log n)|Random or mixed array, decent pivots|
|Worst Case|O(n²)|Sorted/reverse array, poor pivot choices|
|Space|O(log n)|Due to recursion stack (in-place sorting)|

---

### 💡 How to Avoid Worst Case?

Use smarter pivot selection:

- ✅ **Random Pivot**  
    Reduces chances of hitting worst case
    
- ✅ **Median-of-Three**  
    Take the median of first, middle, and last element as pivot
    
- ✅ **Hybrid Sorting**  
    Switch to **Insertion Sort** when subarrays become small
    

---

### 🧪 Real-Life Note:

Even though **worst case is O(n²)**, in **practical usage** Quick Sort is often **faster** than Merge Sort or Heap Sort due to:

- Better cache performance
    
- In-place sorting (low memory usage)
    
- Fewer comparisons on average
    

---

# What is Stable Sorting?

A **sorting algorithm is stable** if:

> **When two elements have equal keys (values), they appear in the same order in the sorted output as they did in the input.**

---

### 🔍 Example to Understand Stability:

Let’s take an array of objects (or tuples) with a name and an age:

```js
[
  { name: "Alice", age: 25 },
  { name: "Bob", age: 30 },
  { name: "Charlie", age: 25 }
]
```

If you **sort by age**, a **stable sort** will maintain the relative order of **Alice and Charlie**, since both have `age = 25`, and **Alice came before Charlie** originally.

### ✅ Stable Sort Output:

```js
[
  { name: "Alice", age: 25 },
  { name: "Charlie", age: 25 },
  { name: "Bob", age: 30 }
]
```

### ❌ Unstable Sort Output (possible):

```js
[
  { name: "Charlie", age: 25 },
  { name: "Alice", age: 25 },
  { name: "Bob", age: 30 }
]
```

Here, the relative order of `Alice` and `Charlie` is lost — this is **not stable**.

---

## 🔄 Why Does Stability Matter?

### 1. **Multi-Level Sorting**

If you want to:

- First sort a list by **age**
    
- Then sort by **name**
    

A **stable sort** allows the first-level sorting order to **remain intact** for duplicate values.

### 2. **Data Integrity**

In real systems like DBs, reports, or user interfaces — keeping the original order of equal elements is important for **consistency and readability**.

### 3. **Chained Sorting**

In libraries or frameworks where multiple sorting conditions are applied, stability ensures that earlier sort conditions aren’t destroyed by later ones.

---

## 🧪 Examples of Stable and Unstable Sorting Algorithms

|Algorithm|Stable?|
|---|---|
|✅ Bubble Sort|Yes|
|✅ Insertion Sort|Yes|
|✅ Merge Sort|Yes|
|✅ Tim Sort|Yes (used in Python & Java)|
|❌ Quick Sort|No (unless modified)|
|❌ Heap Sort|No|
|❌ Selection Sort|No|

🧠 Note: Some unstable algorithms **can be made stable**, but at the cost of extra space or complexity.

---

## 🧰 How to Make an Unstable Sort Stable (Basic Idea)

You can **track original positions** in a secondary array or add metadata:

```js
[{ value: 25, index: 0 }, { value: 25, index: 1 }]
```

Then, when comparing two equal values, you check their original index to preserve the order.

---

## ⏱️ Time and Space Cost of Stability

- **Stable sorts may use extra space** (like Merge Sort needs O(n) extra memory)
    
- **In-place stable sorts** like Insertion Sort and Bubble Sort exist but can be slow (O(n²))
    

That's why practical stable and fast sorts like **TimSort** are used in real-life apps (e.g. `Array.prototype.sort()` in modern JS is stable as of ECMAScript 2019).

---

## 🔑 TL;DR Summary

|Feature|Description|
|---|---|
|**Stable Sort**|Preserves order of equal elements|
|**Useful For**|Multi-level sort, consistency in output|
|**Examples (Stable)**|Merge, Insertion, Bubble, TimSort|
|**Examples (Unstable)**|Quick, Heap, Selection|
|**Trade-offs**|Stability may cost extra space or time|

---

Let me know if you want to implement a **stable vs unstable sort demo in JS**, or need it explained with objects, tables, or visuals — I got you covered bro 💻💯

