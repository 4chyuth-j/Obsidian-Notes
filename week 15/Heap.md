# 🚀Heap Data Structure in JavaScript

A heap is a specialized tree-based data structure that satisfies the **heap property**. In JavaScript, heaps are commonly implemented as binary heaps (either min-heaps or max-heaps) using arrays.

## What is a Heap?

A heap is a complete binary tree where:
- In a **min-heap**, each parent node is less than or equal to its child nodes (smallest element at root)
- In a **max-heap**, each parent node is greater than or equal to its child nodes (largest element at root)

### Key Characteristics:
- **Complete binary tree**: All levels are fully filled except possibly the last level, which is filled from left to right
- **Heap property**: The ordering of parent and child nodes is maintained throughout the structure

## Implementation in JavaScript

Here's a basic implementation of a min-heap in JavaScript:

```javascript
class MinHeap {
  constructor() {
    this.heap = [];
  }

  // Helper methods to get parent and child indices
  getParentIndex(index) { return Math.floor((index - 1) / 2); }
  getLeftChildIndex(index) { return 2 * index + 1; }
  getRightChildIndex(index) { return 2 * index + 2; }

  // Swap two elements in the heap
  swap(index1, index2) {
    [this.heap[index1], this.heap[index2]] = [this.heap[index2], this.heap[index1]];
  }

  // Insert a new element
  insert(value) {
    this.heap.push(value);
    this.heapifyUp();
  }

  // Remove and return the minimum element
  extractMin() {
    if (this.heap.length === 0) return null;
    const min = this.heap[0];
    const last = this.heap.pop();
    if (this.heap.length > 0) {
      this.heap[0] = last;
      this.heapifyDown();
    }
    return min;
  }

  // Move element up to maintain heap property
  heapifyUp() {
    let index = this.heap.length - 1;
    while (index > 0) {
      const parentIndex = this.getParentIndex(index);
      if (this.heap[parentIndex] <= this.heap[index]) break;
      this.swap(parentIndex, index);
      index = parentIndex;
    }
  }

  // Move element down to maintain heap property
  heapifyDown() {
    let index = 0;
    const length = this.heap.length;
    while (true) {
      const leftChildIndex = this.getLeftChildIndex(index);
      const rightChildIndex = this.getRightChildIndex(index);
      let smallest = index;
      
      if (leftChildIndex < length && this.heap[leftChildIndex] < this.heap[smallest]) {
        smallest = leftChildIndex;
      }
      
      if (rightChildIndex < length && this.heap[rightChildIndex] < this.heap[smallest]) {
        smallest = rightChildIndex;
      }
      
      if (smallest === index) break;
      
      this.swap(index, smallest);
      index = smallest;
    }
  }
}
```

## Uses of Heaps in JavaScript

1. **Priority Queues**: Heaps efficiently support insertion and extraction of the highest (or lowest) priority element
2. **Heap Sort**: An efficient O(n log n) sorting algorithm
3. **Graph Algorithms**:
   - Dijkstra's algorithm for shortest paths
   - Prim's algorithm for minimum spanning trees
4. **Median Maintenance**: Two heaps can efficiently track the median of a stream of numbers
5. **K-th Largest/Smallest Elements**: Quickly find top K elements in a dataset

## Advantages of Heaps

1. **Efficient Operations**:
   - Insertion: O(log n)
   - Extraction of min/max: O(log n)
   - Peek at min/max: O(1)
   
2. **Memory Efficient**: Implemented as an array, so no pointers needed like in other tree structures

3. **Flexible**: Can be used as either min-heap or max-heap based on need

4. **Predictable Performance**: Operations are guaranteed to be logarithmic time

## Disadvantages of Heaps

1. **Not Ideal for Searching**: Searching for an arbitrary element is O(n) since heaps aren't sorted

2. **Limited Access**: Only the root element is directly accessible in constant time

3. **No Ordered Traversal**: Elements aren't stored in sorted order (only partial order is maintained)

4. **Slower than Specialized Structures**: For specific use cases, other structures might be faster:
   - Hash tables for lookups
   - Binary search trees for ordered traversal

## Performance Analysis

| Operation      | Time Complexity | Space Complexity |
|---------------|-----------------|------------------|
| Insert        | O(log n)        | O(1)             |
| Extract Min/Max | O(log n)      | O(1)             |
| Peek Min/Max  | O(1)           | O(1)             |
| Search        | O(n)           | O(1)             |
| Build Heap   | O(n)           | O(n)             |

## Practical Example: Priority Queue

```javascript
// Using our MinHeap as a priority queue
const pq = new MinHeap();
pq.insert({priority: 3, task: "Low priority task"});
pq.insert({priority: 1, task: "High priority task"});
pq.insert({priority: 2, task: "Medium priority task"});

console.log(pq.extractMin()); // {priority: 1, task: "High priority task"}
console.log(pq.extractMin()); // {priority: 2, task: "Medium priority task"}
console.log(pq.extractMin()); // {priority: 3, task: "Low priority task"}
```

## When to Use a Heap in JavaScript

Consider using a heap when:
- You need frequent access to the smallest or largest element
- You're implementing a priority queue
- You need to process elements in order of priority
- You're working with large datasets where O(n log n) operations are acceptable
- You need to frequently merge sorted data streams

## Alternatives to Heaps in JavaScript

1. **Arrays**: For simple cases where performance isn't critical
2. **Binary Search Trees**: When you need ordered traversal or faster searching
3. **Skip Lists**: For more complex priority queue implementations
4. **Fibonacci Heaps**: For advanced graph algorithms with better amortized times

Heaps are a fundamental data structure that every JavaScript developer should understand, especially when working with algorithms or performance-sensitive applications.

# 🚀Priority Queue Implementation in JavaScript

A priority queue is an abstract data type similar to a regular queue, but where each element has a "priority" associated with it. Elements with higher priority are served before elements with lower priority. Here's a complete implementation using a min-heap (lower numbers = higher priority).

## Complete Priority Queue Implementation

```javascript
class PriorityQueue {
  constructor() {
    this.heap = [];
  }

  // Helper methods to get parent and child indices
  #getParentIndex(index) { return Math.floor((index - 1) / 2); }
  #getLeftChildIndex(index) { return 2 * index + 1; }
  #getRightChildIndex(index) { return 2 * index + 2; }

  // Swap two elements in the heap
  #swap(index1, index2) {
    [this.heap[index1], this.heap[index2]] = [this.heap[index2], this.heap[index1]];
  }

  // Check if the queue is empty
  isEmpty() {
    return this.heap.length === 0;
  }

  // Get the size of the queue
  size() {
    return this.heap.length;
  }

  // Peek at the highest priority item without removing it
  peek() {
    if (this.isEmpty()) return null;
    return this.heap[0].value;
  }

  // Enqueue an element with a given priority
  enqueue(value, priority) {
    const element = { value, priority };
    this.heap.push(element);
    this.#heapifyUp();
  }

  // Dequeue the highest priority element
  dequeue() {
    if (this.isEmpty()) return null;
    
    // Swap root with last element
    this.#swap(0, this.heap.length - 1);
    const removedElement = this.heap.pop();
    
    // Restore heap property
    if (!this.isEmpty()) {
      this.#heapifyDown();
    }
    
    return removedElement.value;
  }

  // Move element up to maintain heap property
  #heapifyUp() {
    let currentIndex = this.heap.length - 1;
    
    while (currentIndex > 0) {
      const parentIndex = this.#getParentIndex(currentIndex);
      
      // Compare priorities (lower number = higher priority)
      if (this.heap[parentIndex].priority <= this.heap[currentIndex].priority) break;
      
      this.#swap(parentIndex, currentIndex);
      currentIndex = parentIndex;
    }
  }

  // Move element down to maintain heap property
  #heapifyDown() {
    let currentIndex = 0;
    const length = this.heap.length;
    
    while (true) {
      const leftChildIndex = this.#getLeftChildIndex(currentIndex);
      const rightChildIndex = this.#getRightChildIndex(currentIndex);
      let smallestPriorityIndex = currentIndex;
      
      // Compare with left child
      if (leftChildIndex < length && 
          this.heap[leftChildIndex].priority < this.heap[smallestPriorityIndex].priority) {
        smallestPriorityIndex = leftChildIndex;
      }
      
      // Compare with right child
      if (rightChildIndex < length && 
          this.heap[rightChildIndex].priority < this.heap[smallestPriorityIndex].priority) {
        smallestPriorityIndex = rightChildIndex;
      }
      
      // If no swap needed, we're done
      if (smallestPriorityIndex === currentIndex) break;
      
      // Swap and continue
      this.#swap(currentIndex, smallestPriorityIndex);
      currentIndex = smallestPriorityIndex;
    }
  }

  // Optional: Update priority of an element
  updatePriority(value, newPriority) {
    const index = this.heap.findIndex(item => item.value === value);
    if (index === -1) return false;
    
    const oldPriority = this.heap[index].priority;
    this.heap[index].priority = newPriority;
    
    // Determine which direction to heapify
    if (newPriority < oldPriority) {
      this.#heapifyUp(index);
    } else {
      this.#heapifyDown(index);
    }
    
    return true;
  }
}
```

## How to Use the Priority Queue

```javascript
// Create a priority queue
const pq = new PriorityQueue();

// Enqueue elements with priorities
pq.enqueue("Task 1", 3);  // Low priority
pq.enqueue("Task 2", 1);  // High priority
pq.enqueue("Task 3", 2);  // Medium priority

// Check the queue
console.log(pq.peek());    // "Task 2" (highest priority)
console.log(pq.size());    // 3

// Process elements in priority order
console.log(pq.dequeue()); // "Task 2"
console.log(pq.dequeue()); // "Task 3"
console.log(pq.dequeue()); // "Task 1"

// Check if empty
console.log(pq.isEmpty()); // true
```

## Key Features

1. **Min-Heap Based**: Lower priority numbers indicate higher priority
2. **Core Operations**:
   - `enqueue(value, priority)`: O(log n)
   - `dequeue()`: O(log n)
   - `peek()`: O(1)
3. **Optional Update**: Change priority of existing elements
4. **Private Methods**: Internal heap operations are marked with `#` (private class fields)

## Time Complexity

| Operation      | Time Complexity |
|---------------|-----------------|
| enqueue()     | O(log n)        |
| dequeue()     | O(log n)        |
| peek()        | O(1)            |
| updatePriority() | O(log n)      |
| isEmpty()     | O(1)            |
| size()        | O(1)            |

## Practical Applications

1. **Task Scheduling**: Execute highest priority tasks first
2. **Dijkstra's Algorithm**: For finding shortest paths in graphs
3. **Huffman Coding**: For data compression
4. **Event Simulation**: Process events in chronological order
5. **Bandwidth Management**: Prioritize network packets

This implementation provides a solid foundation that you can extend with additional features like custom comparators or bulk operations as needed.


# 🚀What is Heapify?

**Heapify** is the process of turning a regular array (or a subtree) into a **valid heap**.

It means fixing the heap structure — either **min-heap** or **max-heap** — so that it obeys the rules:

- **Min-heap**: Every parent node is **less than** its children.
    
- **Max-heap**: Every parent node is **greater than** its children.
    

---

## 🔧 When Do We Use Heapify?

1. **When inserting** a new element → you heapify _upward_ (`upHeap` or `heapifyUp`)
    
2. **When removing** the root → you heapify _downward_ (`downHeap` or `heapifyDown`)
    
3. **When building a heap** from a full array → you do a **bottom-up heapify**
    

---

## 🔁 Two Types of Heapify:

### 1. **Heapify Up** (a.k.a. Bubble Up, Sift Up)

Used when you insert an element at the end of the heap.

```txt
Insert 60 ➝ Heapify up by comparing with its parent until it’s in the right place.
```

Example:

```
Before insert:      After insert:

       50               50
     /    \           /    \
   40     30    ➝   40     30
  /  \   /         /  \   / 
20  10  60       20  10  60

HeapifyUp swaps 60 with 30, then 50 (if max heap)
```

---

### 2. **Heapify Down** (a.k.a. Bubble Down, Sift Down)

Used when you remove the root (first element) and move the last element to root.

```txt
Pop root ➝ Move last element to root ➝ Heapify down to fix heap.
```

Example:

```
Before remove:           After moving last to root:

       90                        20
     /    \       ➝           /    \
   60     70                60     70
  /  \                       /  
20  10                     10

HeapifyDown: 20 swapped with 70 → then maybe again
```

---

## 🏗️ Heapify While Building a Heap (Heapify Entire Array)

If you have an **unsorted array** like `[5, 3, 8, 4, 1, 2]`, and want to turn it into a heap:

- You **start from the last parent node**
    
- Call `heapifyDown()` on each node from bottom to top
    

This takes **O(n)** time, surprisingly efficient.

---

## 🔥 Real-World Analogy

Imagine a pyramid of people sorted by height (tallest on top for max-heap):

- If a new person joins at the bottom who's taller than their "parent", you bubble them up.
    
- If the tallest person leaves, you replace them with a short person and fix the pyramid top-down.
    

That fixing process = **heapify**.

---

## ✅ Summary

|Term|Meaning|When Used|
|---|---|---|
|`heapifyUp`|Fixes heap by going **up**|After insertion|
|`heapifyDown`|Fixes heap by going **down**|After removal or building heap|
|`heapify()`|A general term for fixing heap|Both up & down directions|

---

Want me to show the JS code of `heapifyDown` and `heapifyUp` step by step? Or how it's used in `heapSort`? Just say the word, bro 👊💻
























