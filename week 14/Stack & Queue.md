# **Stack in JavaScript: In-Depth Guide**

A **stack** is a fundamental **Last-In-First-Out (LIFO)** data structure where the last element added is the first one removed. It's widely used in programming for tasks like function call management, undo/redo operations, and parsing expressions.

---

## **1. Stack Implementation in JavaScript**
JavaScript doesn't have a built-in `Stack` class, but we can easily implement one using:
- **Arrays** (with `push()` and `pop()`), or
- **Linked Lists** (for a more optimized version).

### **Basic Array-Based Stack**
```javascript
class Stack {
  constructor() {
    this.items = [];
  }

  // Push element onto stack (O(1))
  push(element) {
    this.items.push(element);
  }

  // Pop element from stack (O(1))
  pop() {
    if (this.isEmpty()) return "Stack is empty";
    return this.items.pop();
  }

  // Peek at top element (O(1))
  peek() {
    if (this.isEmpty()) return "Stack is empty";
    return this.items[this.items.length - 1];
  }

  // Check if stack is empty (O(1))
  isEmpty() {
    return this.items.length === 0;
  }

  // Get stack size (O(1))
  size() {
    return this.items.length;
  }

  // Print stack (O(n))
  print() {
    console.log(this.items);
  }
}

// Usage
const stack = new Stack();
stack.push(10);
stack.push(20);
stack.push(30);
stack.print(); // [10, 20, 30]
console.log(stack.pop()); // 30
console.log(stack.peek()); // 20
console.log(stack.size()); // 2
```

---

## **2. Key Stack Operations & Time Complexity**
| Operation | Method | Time Complexity | Description |
|-----------|--------|-----------------|-------------|
| **Push** | `push()` | O(1) | Adds an element to the top |
| **Pop** | `pop()` | O(1) | Removes the top element |
| **Peek** | `peek()` | O(1) | Returns the top element without removing it |
| **IsEmpty** | `isEmpty()` | O(1) | Checks if the stack is empty |
| **Size** | `size()` | O(1) | Returns the number of elements |

---

## **3. Practical Applications of Stacks**
### **1. Function Call Stack**
- JavaScript uses a **call stack** to manage function execution.
- When a function is called, it's pushed onto the stack.
- When it returns, it's popped off.

```javascript
function first() { second(); }
function second() { third(); }
function third() { console.trace(); } // Prints call stack

first(); // Stack: first → second → third
```

### **2. Undo/Redo Operations**
- Stacks store actions in order (e.g., text editor undo/redo).
```javascript
const undoStack = [];
const redoStack = [];

function type(text) {
  undoStack.push(text);
}

function undo() {
  const lastAction = undoStack.pop();
  if (lastAction) redoStack.push(lastAction);
}

type("Hello");
type("World");
undo(); // Removes "World" (moves to redo stack)
```

### **3. Balanced Parentheses Checker**
- Used in compilers to validate syntax.
```javascript
function isBalanced(expr) {
  const stack = [];
  const pairs = { '(': ')', '[': ']', '{': '}' };

  for (const char of expr) {
    if (pairs[char]) stack.push(char); // Push opening brackets
    else if (char === ')' || char === ']' || char === '}') {
      if (pairs[stack.pop()] !== char) return false;
    }
  }

  return stack.length === 0;
}

console.log(isBalanced("({[]})")); // true
console.log(isBalanced("({[})")); // false
```

### **4. Backtracking (Maze Solving, DFS)**
- Stacks help in **Depth-First Search (DFS)** algorithms.
```javascript
// Simplified DFS using a stack
function dfs(graph, start) {
  const stack = [start];
  const visited = new Set();

  while (stack.length) {
    const node = stack.pop();
    if (!visited.has(node)) {
      visited.add(node);
      console.log(node);
      for (const neighbor of graph[node]) {
        stack.push(neighbor);
      }
    }
  }
}

const graph = {
  'A': ['B', 'C'],
  'B': ['D'],
  'C': ['E'],
  'D': ['F'],
  'E': [],
  'F': []
};

dfs(graph, 'A'); // A → C → E → B → D → F
```

---

## **4. Stack vs. Other Data Structures**
| Structure | Order | Key Operations | Use Case |
|-----------|-------|----------------|----------|
| **Stack** | LIFO | `push()`, `pop()` | Function calls, undo/redo |
| **Queue** | FIFO | `enqueue()`, `dequeue()` | Task scheduling, BFS |
| **Array** | Indexed | `push()`, `pop()`, `shift()` | General-purpose lists |
| **Set** | Unique | `add()`, `has()`, `delete()` | Membership checks |

---

## **5. Advanced: Optimized Stack (Linked List)**
For better performance (avoiding array resizing), we can use a **singly linked list**:
```javascript
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

class LinkedListStack {
  constructor() {
    this.top = null;
    this.size = 0;
  }

  push(value) {
    const newNode = new Node(value);
    newNode.next = this.top;
    this.top = newNode;
    this.size++;
  }

  pop() {
    if (!this.top) return null;
    const poppedValue = this.top.value;
    this.top = this.top.next;
    this.size--;
    return poppedValue;
  }

  peek() {
    return this.top?.value;
  }

  isEmpty() {
    return this.size === 0;
  }
}

const llStack = new LinkedListStack();
llStack.push(10);
llStack.push(20);
console.log(llStack.pop()); // 20
```

---

## **6. When to Use a Stack?**
✔ **Need LIFO behavior** (last-in-first-out).  
✔ **Managing function calls** (recursion, execution context).  
✔ **Undo/Redo operations** (e.g., text editors).  
✔ **Syntax parsing** (e.g., checking balanced brackets).  
✔ **DFS (Depth-First Search)** in graph algorithms.  

---

## **Final Summary**
| Concept | Explanation |
|---------|-------------|
| **Definition** | LIFO (Last-In-First-Out) data structure |
| **Core Methods** | `push()`, `pop()`, `peek()`, `isEmpty()`, `size()` |
| **Time Complexity** | O(1) for all key operations |
| **Applications** | Call stack, undo/redo, DFS, syntax validation |
| **Implementation** | Arrays (simple) or Linked Lists (optimized) |


# How stacks are used in undo-redo operations?
## 1️⃣ What is Undo-Redo?

- **Undo:** Reverse the last action.
    
- **Redo:** Re-apply the action you just undid.
    

---

## 2️⃣ Why use **Stacks**?

Stacks use **LIFO (Last In, First Out)** behavior:

- The **last action performed** should be the **first action undone**.
    
- Perfect for undo-redo workflows.
    

---

## 3️⃣ **How it works using Two Stacks:**

✅ **Stack 1: Undo Stack**

- Stores all actions performed by the user.
    
- When the user presses **Undo**, pop the last action from the Undo Stack and perform its reverse action.
    

✅ **Stack 2: Redo Stack**

- Stores actions that have been undone.
    
- When the user presses **Redo**, pop from the Redo Stack and perform the action again.
    

---

## 4️⃣ **Step-by-Step Example:**

### Scenario:

You are typing:

- **Type 'A'**
    
- **Type 'B'**
    
- **Type 'C'**
    

### Stacks after typing:

```
Undo Stack: ['A', 'B', 'C']
Redo Stack: []
```

---

### **Press Undo:**

- Pop 'C' from Undo Stack.
    
- Remove 'C' from the text.
    
- Push 'C' onto Redo Stack.
    

Now:

```
Undo Stack: ['A', 'B']
Redo Stack: ['C']
```

---

### **Press Undo again:**

- Pop 'B' from Undo Stack.
    
- Remove 'B' from the text.
    
- Push 'B' onto Redo Stack.
    

Now:

```
Undo Stack: ['A']
Redo Stack: ['C', 'B']
```

---

### **Press Redo:**

- Pop 'B' from Redo Stack.
    
- Add 'B' back to the text.
    
- Push 'B' back onto Undo Stack.
    

Now:

```
Undo Stack: ['A', 'B']
Redo Stack: ['C']
```

---

### **Perform new action after undo:**

If you type 'D' now:

- The **Redo Stack is cleared**.
    
- 'D' is pushed onto the Undo Stack.
    

Now:

```
Undo Stack: ['A', 'B', 'D']
Redo Stack: []
```

This ensures redo actions remain consistent with user actions.

---

## 5️⃣ **Simple JavaScript Implementation**

```javascript
class UndoRedo {
    constructor() {
        this.undoStack = [];
        this.redoStack = [];
    }

    performAction(action) {
        this.undoStack.push(action);
        this.redoStack = []; // clear redo stack on new action
        console.log(`Performed: ${action}`);
    }

    undo() {
        if (this.undoStack.length === 0) {
            console.log("Nothing to undo");
            return;
        }
        const action = this.undoStack.pop();
        this.redoStack.push(action);
        console.log(`Undo: ${action}`);
    }

    redo() {
        if (this.redoStack.length === 0) {
            console.log("Nothing to redo");
            return;
        }
        const action = this.redoStack.pop();
        this.undoStack.push(action);
        console.log(`Redo: ${action}`);
    }

    showStacks() {
        console.log(`Undo Stack: [${this.undoStack.join(', ')}]`);
        console.log(`Redo Stack: [${this.redoStack.join(', ')}]`);
    }
}

// Usage:
const editor = new UndoRedo();

editor.performAction('Type A');
editor.performAction('Type B');
editor.performAction('Type C');

editor.showStacks();

editor.undo();
editor.undo();

editor.showStacks();

editor.redo();

editor.showStacks();

editor.performAction('Type D');

editor.showStacks();
```

---

## ✅ Summary:

- Use **two stacks for undo-redo**:
    
    - **Undo Stack** → store performed actions.
        
    - **Redo Stack** → store undone actions.
        
- On **Undo**, pop from Undo, push to Redo.
    
- On **Redo**, pop from Redo, push to Undo.
    
- On **new action after undo**, clear Redo stack.
    

---

If you want:  
✅ A **diagram showing arrows and stacks** for your notes.  
✅ Real-world **text editor simulation code** with undo-redo for practice.  
✅ A **DSA interview explanation cheat sheet** on this concept.

let me know!
# **Queue in JavaScript: In-Depth Guide**

A **Queue** is a **First-In-First-Out (FIFO)** data structure where the first element added is the first one removed. It's widely used in scenarios like task scheduling, printer queues, and breadth-first search (BFS) algorithms.

---

## **1. Queue Implementation in JavaScript**
JavaScript doesn't have a built-in `Queue` class, but we can implement it using:
- **Arrays** (with `push()` and `shift()`), or
- **Linked Lists** (for better performance).

### **Basic Array-Based Queue**
```javascript
class Queue {
  constructor() {
    this.items = [];
  }

  // Enqueue: Add element to the back (O(1))
  enqueue(element) {
    this.items.push(element);
  }

  // Dequeue: Remove element from the front (O(n) with arrays, O(1) with linked lists)
  dequeue() {
    if (this.isEmpty()) return "Queue is empty";
    return this.items.shift();
  }

  // Peek at front element (O(1))
  front() {
    if (this.isEmpty()) return "Queue is empty";
    return this.items[0];
  }

  // Check if queue is empty (O(1))
  isEmpty() {
    return this.items.length === 0;
  }

  // Get queue size (O(1))
  size() {
    return this.items.length;
  }

  // Print queue (O(n))
  print() {
    console.log(this.items);
  }
}

// Usage
const queue = new Queue();
queue.enqueue(10);
queue.enqueue(20);
queue.enqueue(30);
queue.print(); // [10, 20, 30]
console.log(queue.dequeue()); // 10
console.log(queue.front()); // 20
console.log(queue.size()); // 2
```

---

## **2. Key Queue Operations & Time Complexity**
| Operation | Method | Time Complexity | Description |
|-----------|--------|-----------------|-------------|
| **Enqueue** | `enqueue()` | O(1) | Adds an element to the back |
| **Dequeue** | `dequeue()` | O(n) (with arrays) / O(1) (with linked lists) | Removes the front element |
| **Front** | `front()` | O(1) | Returns the front element without removing it |
| **IsEmpty** | `isEmpty()` | O(1) | Checks if the queue is empty |
| **Size** | `size()` | O(1) | Returns the number of elements |

---

## **3. Practical Applications of Queues**
### **1. Task Scheduling (Event Loop in JavaScript)**
- JavaScript's **event loop** uses a **task queue** to manage asynchronous operations.
```javascript
console.log("Start");
setTimeout(() => console.log("Timeout 1"), 0);
Promise.resolve().then(() => console.log("Promise"));
console.log("End");
// Output: Start → End → Promise → Timeout 1
```

### **2. Printer Queue**
- Print jobs are processed in the order they are received.
```javascript
const printerQueue = new Queue();
printerQueue.enqueue("Document1.pdf");
printerQueue.enqueue("Document2.pdf");
printerQueue.enqueue("Document3.pdf");

while (!printerQueue.isEmpty()) {
  console.log(`Printing: ${printerQueue.dequeue()}`);
}
// Output: Printing: Document1.pdf → Document2.pdf → Document3.pdf
```

### **3. Breadth-First Search (BFS)**
- Queues are essential for **BFS** in graphs/trees.
```javascript
function bfs(graph, start) {
  const queue = [start];
  const visited = new Set();

  while (queue.length) {
    const node = queue.shift();
    if (!visited.has(node)) {
      visited.add(node);
      console.log(node);
      for (const neighbor of graph[node]) {
        queue.push(neighbor);
      }
    }
  }
}

const graph = {
  'A': ['B', 'C'],
  'B': ['D'],
  'C': ['E'],
  'D': ['F'],
  'E': [],
  'F': []
};

bfs(graph, 'A'); // A → B → C → D → E → F
```

### **4. CPU Scheduling (Round-Robin)**
- Queues manage processes in operating systems.
```javascript
const processQueue = new Queue();
processQueue.enqueue("P1");
processQueue.enqueue("P2");
processQueue.enqueue("P3");

while (!processQueue.isEmpty()) {
  const currentProcess = processQueue.dequeue();
  console.log(`Executing ${currentProcess}`);
  // Simulate time slice
  if (Math.random() > 0.5) {
    processQueue.enqueue(currentProcess); // Re-add if not finished
  }
}
```

---

## **4. Queue vs. Other Data Structures**
| Structure | Order | Key Operations | Use Case |
|-----------|-------|----------------|----------|
| **Queue** | FIFO | `enqueue()`, `dequeue()` | Task scheduling, BFS |
| **Stack** | LIFO | `push()`, `pop()` | Function calls, undo/redo |
| **Array** | Indexed | `push()`, `pop()`, `shift()` | General-purpose lists |
| **Priority Queue** | Sorted | `insert()`, `extractMax()` | Dijkstra's algorithm |

---

## **5. Advanced: Optimized Queue (Linked List)**
To avoid O(n) `shift()` operations in arrays, use a **linked list**:
```javascript
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

class LinkedListQueue {
  constructor() {
    this.front = null;
    this.rear = null;
    this.size = 0;
  }

  enqueue(value) {
    const newNode = new Node(value);
    if (!this.front) {
      this.front = newNode;
      this.rear = newNode;
    } else {
      this.rear.next = newNode;
      this.rear = newNode;
    }
    this.size++;
  }

  dequeue() {
    if (!this.front) return null;
    const dequeuedValue = this.front.value;
    this.front = this.front.next;
    if (!this.front) this.rear = null;
    this.size--;
    return dequeuedValue;
  }

  peek() {
    return this.front?.value;
  }

  isEmpty() {
    return this.size === 0;
  }
}

const llQueue = new LinkedListQueue();
llQueue.enqueue(10);
llQueue.enqueue(20);
console.log(llQueue.dequeue()); // 10
```

---

## **6. Specialized Queues**
### **1. Circular Queue**
- Fixed-size queue that reuses empty slots.
```javascript
class CircularQueue {
  constructor(capacity) {
    this.items = new Array(capacity);
    this.capacity = capacity;
    this.front = -1;
    this.rear = -1;
  }

  enqueue(element) {
    if (this.isFull()) return false;
    if (this.isEmpty()) this.front = 0;
    this.rear = (this.rear + 1) % this.capacity;
    this.items[this.rear] = element;
    return true;
  }

  dequeue() {
    if (this.isEmpty()) return null;
    const element = this.items[this.front];
    if (this.front === this.rear) {
      this.front = -1;
      this.rear = -1;
    } else {
      this.front = (this.front + 1) % this.capacity;
    }
    return element;
  }

  isFull() {
    return (this.rear + 1) % this.capacity === this.front;
  }

  isEmpty() {
    return this.front === -1;
  }
}
```

### **2. Priority Queue**
- Elements are dequeued based on priority (not order).
```javascript
class PriorityQueue {
  constructor() {
    this.items = [];
  }

  enqueue(element, priority) {
    const queueElement = { element, priority };
    let added = false;
    for (let i = 0; i < this.items.length; i++) {
      if (queueElement.priority < this.items[i].priority) {
        this.items.splice(i, 0, queueElement);
        added = true;
        break;
      }
    }
    if (!added) this.items.push(queueElement);
  }

  dequeue() {
    return this.items.shift();
  }
}

const pq = new PriorityQueue();
pq.enqueue("Task 1", 2);
pq.enqueue("Task 2", 1);
console.log(pq.dequeue()); // { element: "Task 2", priority: 1 }
```

---

## **7. When to Use a Queue?**
✔ **Need FIFO behavior** (first-in-first-out).  
✔ **Task scheduling** (e.g., event loop, printer queues).  
✔ **BFS (Breadth-First Search)** in graph algorithms.  
✔ **Buffering data** (e.g., streaming, message brokers).  

---

## **Final Summary**
| Concept | Explanation |
|---------|-------------|
| **Definition** | FIFO (First-In-First-Out) data structure |
| **Core Methods** | `enqueue()`, `dequeue()`, `front()`, `isEmpty()`, `size()` |
| **Time Complexity** | O(1) for enqueue, O(n) for dequeue (with arrays) |
| **Applications** | Task scheduling, BFS, CPU scheduling |
| **Implementation** | Arrays (simple) or Linked Lists (optimized) |





# **Types of Queues in JavaScript: Comprehensive Guide**

Queues come in several specialized forms, each designed for specific use cases. Here's a detailed breakdown of all major queue types with implementations and real-world applications.

---

## **1. Standard Queue (Linear Queue)**
**FIFO (First-In-First-Out)** structure with basic operations.

### **Implementation**
```javascript
class Queue {
  constructor() {
    this.items = [];
  }

  enqueue(item) {
    this.items.push(item);
  }

  dequeue() {
    return this.items.shift();
  }

  peek() {
    return this.items[0];
  }

  isEmpty() {
    return this.items.length === 0;
  }
}
```

### **Use Cases**
- Printer job scheduling
- Breadth-First Search (BFS)
- Call center systems

---

## **2. Circular Queue**
Fixed-size queue that reuses empty slots when full (efficient memory usage).

### **Implementation**
```javascript
class CircularQueue {
  constructor(capacity) {
    this.items = new Array(capacity);
    this.capacity = capacity;
    this.front = -1;
    this.rear = -1;
  }

  enqueue(item) {
    if (this.isFull()) return false;
    
    if (this.isEmpty()) this.front = 0;
    this.rear = (this.rear + 1) % this.capacity;
    this.items[this.rear] = item;
    return true;
  }

  dequeue() {
    if (this.isEmpty()) return null;
    
    const item = this.items[this.front];
    if (this.front === this.rear) {
      this.front = -1;
      this.rear = -1;
    } else {
      this.front = (this.front + 1) % this.capacity;
    }
    return item;
  }

  isFull() {
    return (this.rear + 1) % this.capacity === this.front;
  }

  isEmpty() {
    return this.front === -1;
  }
}
```

### **Use Cases**
- Traffic light control systems
- Memory management in OS
- Streaming data buffers

---

## **3. Priority Queue**
Elements are processed based on priority rather than insertion order.

### **Implementation (Min-Heap Priority)**
```javascript
class PriorityQueue {
  constructor() {
    this.heap = [];
  }

  enqueue(item, priority) {
    this.heap.push({ item, priority });
    this.#heapifyUp();
  }

  dequeue() {
    if (this.isEmpty()) return null;
    
    const root = this.heap[0];
    const last = this.heap.pop();
    
    if (this.heap.length > 0) {
      this.heap[0] = last;
      this.#heapifyDown();
    }
    
    return root.item;
  }

  #heapifyUp() {
    let index = this.heap.length - 1;
    while (index > 0) {
      const parentIndex = Math.floor((index - 1) / 2);
      if (this.heap[parentIndex].priority <= this.heap[index].priority) break;
      [this.heap[parentIndex], this.heap[index]] = [this.heap[index], this.heap[parentIndex]];
      index = parentIndex;
    }
  }

  #heapifyDown() {
    let index = 0;
    while (true) {
      const leftChild = 2 * index + 1;
      const rightChild = 2 * index + 2;
      let smallest = index;

      if (leftChild < this.heap.length && 
          this.heap[leftChild].priority < this.heap[smallest].priority) {
        smallest = leftChild;
      }

      if (rightChild < this.heap.length && 
          this.heap[rightChild].priority < this.heap[smallest].priority) {
        smallest = rightChild;
      }

      if (smallest === index) break;
      [this.heap[index], this.heap[smallest]] = [this.heap[smallest], this.heap[index]];
      index = smallest;
    }
  }

  isEmpty() {
    return this.heap.length === 0;
  }
}
```

### **Use Cases**
- Emergency room triage systems
- Dijkstra's shortest path algorithm
- CPU task scheduling

---

## **4. Double-Ended Queue (Deque)**
Allows insertion/deletion at both ends.

### **Implementation**
```javascript
class Deque {
  constructor() {
    this.items = [];
  }

  addFront(item) {
    this.items.unshift(item);
  }

  addRear(item) {
    this.items.push(item);
  }

  removeFront() {
    return this.items.shift();
  }

  removeRear() {
    return this.items.pop();
  }

  isEmpty() {
    return this.items.length === 0;
  }
}
```

### **Use Cases**
- Browser history (back/forward navigation)
- Palindrome checking
- Sliding window algorithms

---

## **5. Blocking Queue**
Thread-safe queue that blocks when empty/full (simulated in JS).

### **Implementation (Promise-based)**
```javascript
class BlockingQueue {
  constructor() {
    this.queue = [];
    this.resolvers = [];
  }

  async enqueue(item) {
    if (this.resolvers.length > 0) {
      const resolve = this.resolvers.shift();
      resolve(item);
    } else {
      this.queue.push(item);
    }
  }

  async dequeue() {
    if (this.queue.length > 0) {
      return Promise.resolve(this.queue.shift());
    } else {
      return new Promise(resolve => {
        this.resolvers.push(resolve);
      });
    }
  }
}
```

### **Use Cases**
- Producer-consumer problems
- Message queues in distributed systems
- Async task processing

---

## **6. Bounded Queue (Fixed Capacity)**
Queue with maximum capacity that rejects new items when full.

### **Implementation**
```javascript
class BoundedQueue {
  constructor(capacity) {
    this.items = [];
    this.capacity = capacity;
  }

  enqueue(item) {
    if (this.items.length >= this.capacity) {
      throw new Error("Queue is full");
    }
    this.items.push(item);
  }

  dequeue() {
    return this.items.shift();
  }

  isFull() {
    return this.items.length === this.capacity;
  }
}
```

### **Use Cases**
- Rate-limiting systems
- Fixed-size caches
- Hardware interrupt handling

---

## **Comparison Table of Queue Types**
| Queue Type | Key Feature | Time Complexity | Use Case Example |
|------------|------------|----------------|------------------|
| **Standard** | Basic FIFO | Enqueue: O(1), Dequeue: O(n) | Printer spooling |
| **Circular** | Reuses space | Enqueue/Dequeue: O(1) | Traffic systems |
| **Priority** | Ordered processing | Enqueue/Dequeue: O(log n) | Hospital triage |
| **Deque** | Double-ended ops | All ops: O(1) | Browser history |
| **Blocking** | Waits for space/data | Async operations | Message brokers |
| **Bounded** | Fixed capacity | O(1) operations | Rate limiting |

---

## **When to Use Which Queue?**
1. **Need basic FIFO?** → Standard Queue
2. **Memory efficiency needed?** → Circular Queue
3. **Priority-based processing?** → Priority Queue
4. **Operations at both ends?** → Deque
5. **Thread-safe operations?** → Blocking Queue (simulated)
6. **Fixed capacity requirement?** → Bounded Queue



# Circular Queue in JavaScript: An In-Depth Explanation

A circular queue (also known as a ring buffer) is a linear data structure that follows the FIFO (First In First Out) principle, but with a key difference from a regular queue - when the rear reaches the end of the queue, it wraps around to the beginning.

## Basic Concept

In a standard queue, once the rear reaches the end of the array/queue, you can't add more elements even if there's space at the front (due to dequeuing). A circular queue solves this by connecting the end of the queue back to the front, forming a circle.

![[Pasted image 20250630163538.png]]

![[Pasted image 20250630163912.png]]
## Implementation in JavaScript

Here's how to implement a circular queue in JavaScript:

```javascript
class CircularQueue {
  constructor(k) {
    this.size = k;
    this.queue = new Array(k);
    this.front = -1;
    this.rear = -1;
  }

  // Add an element to the queue
  enQueue(value) {
    if (this.isFull()) {
      return false;
    }
    if (this.isEmpty()) {
      this.front = 0;
    }
    this.rear = (this.rear + 1) % this.size;
    this.queue[this.rear] = value;
    return true;
  }

  // Remove an element from the queue
  deQueue() {
    if (this.isEmpty()) {
      return false;
    }
    if (this.front === this.rear) {
      this.front = -1;
      this.rear = -1;
      return true;
    }
    this.front = (this.front + 1) % this.size;
    return true;
  }

  // Get the front item
  Front() {
    if (this.isEmpty()) {
      return -1;
    }
    return this.queue[this.front];
  }

  // Get the last item
  Rear() {
    if (this.isEmpty()) {
      return -1;
    }
    return this.queue[this.rear];
  }

  // Check if the queue is empty
  isEmpty() {
    return this.front === -1;
  }

  // Check if the queue is full
  isFull() {
    return (this.rear + 1) % this.size === this.front;
  }
}
```

## Key Operations

1. **enQueue(value)**: Adds an item to the queue. Returns true if successful.
2. **deQueue()**: Removes an item from the queue. Returns true if successful.
3. **Front()**: Gets the front item from the queue.
4. **Rear()**: Gets the last item from the queue.
5. **isEmpty()**: Checks whether the queue is empty.
6. **isFull()**: Checks whether the queue is full.

## Advantages of Circular Queue

1. **Efficient Space Utilization**: Reuses empty spaces created after dequeuing.
2. **Better Performance**: O(1) time complexity for both enqueue and dequeue operations.
3. **Fixed Memory Usage**: Doesn't require dynamic resizing, making it memory efficient.
4. **Predictable Performance**: Consistent performance regardless of operations count.
5. **Useful for Buffering**: Ideal for scenarios where you need a fixed-size buffer.

## Disadvantages of Circular Queue

1. **Fixed Size**: The size is predetermined and cannot be changed dynamically.
2. **Complex Implementation**: More complex to implement than a simple queue.
3. **Wasted Space**: If not managed properly, one slot is often left empty to distinguish between full and empty states.
4. **Not Built-in**: JavaScript doesn't have a built-in circular queue implementation.

## Use Cases

1. **CPU Scheduling**: Operating systems use circular queues for process scheduling.
2. **Memory Management**: Memory is often managed using circular queue concepts.
3. **Traffic Systems**: Traffic light control systems use circular queues.
4. **Streaming Data**: Media players use circular buffers for streaming audio/video.
5. **Producer-Consumer Problems**: Where producers add data and consumers remove data.
6. **Keyboard Buffer**: To store keystrokes before they're processed.
7. **Network Data Packets**: For handling incoming data packets in networking.

## Practical Example: Task Scheduler

```javascript
class TaskScheduler {
  constructor(maxTasks) {
    this.taskQueue = new CircularQueue(maxTasks);
  }
  
  addTask(task) {
    if (this.taskQueue.isFull()) {
      console.log("Queue full - executing oldest task to make space");
      this.taskQueue.deQueue();
    }
    this.taskQueue.enQueue(task);
    console.log(`Added task: ${task}`);
  }
  
  executeNext() {
    if (this.taskQueue.isEmpty()) {
      console.log("No tasks to execute");
      return;
    }
    const task = this.taskQueue.Front();
    this.taskQueue.deQueue();
    console.log(`Executing task: ${task}`);
    return task;
  }
  
  currentTasks() {
    if (this.taskQueue.isEmpty()) return [];
    
    let tasks = [];
    let current = this.taskQueue.front;
    
    do {
      tasks.push(this.taskQueue.queue[current]);
      current = (current + 1) % this.taskQueue.size;
    } while (current !== (this.taskQueue.rear + 1) % this.taskQueue.size);
    
    return tasks;
  }
}

// Usage
const scheduler = new TaskScheduler(3);
scheduler.addTask("Backup database");
scheduler.addTask("Generate report");
scheduler.addTask("Send emails");
scheduler.addTask("Clean temp files"); // Will replace the oldest task

console.log("Current tasks:", scheduler.currentTasks());
scheduler.executeNext();
console.log("Remaining tasks:", scheduler.currentTasks());
```

## When to Choose Circular Queue Over Regular Queue

- When you need a fixed-size buffer
- When you want to prevent memory reallocation
- When you need efficient O(1) enqueue/dequeue operations
- When you're dealing with continuous data streams
- When you need to implement a cache with a size limit

## Performance Considerations

- All operations (enqueue, dequeue, front, rear, isEmpty, isFull) are O(1) time complexity
- Space complexity is O(n) where n is the fixed size of the queue
- More memory efficient than dynamic queues for fixed-size requirements
- Avoids memory fragmentation issues

Circular queues are particularly useful in systems programming, embedded systems, and performance-critical applications where predictable behavior and fixed memory usage are important.




# Implementing a Stack Using Queues 

A stack is a Last-In-First-Out (LIFO) data structure, while a queue is First-In-First-Out (FIFO). Implementing a stack using queues might seem tricky, but it's a great exercise to understand both data structures better.

## Understanding the Problem

**Stack Operations:**
- `push(item)`: Add an item to the top
- `pop()`: Remove and return the top item
- `peek()`: View the top item without removing
- `isEmpty()`: Check if stack is empty

**Queue Operations:**
- `enqueue(item)`: Add to the back
- `dequeue()`: Remove from the front
- `peek()`: View front item
- `isEmpty()`: Check if queue is empty

## Approach 1: Using Two Queues (Push Efficient)

This method makes the `push` operation efficient (O(1)) while `pop` becomes O(n).

```javascript
class StackUsingQueues {
  constructor() {
    this.q1 = []; // Main queue
    this.q2 = []; // Temporary queue
  }

  // O(1) operation
  push(item) {
    this.q1.push(item);
  }

  // O(n) operation
  pop() {
    if (this.isEmpty()) {
      return undefined;
    }

    // Move all items except last from q1 to q2
    while (this.q1.length > 1) {
      this.q2.push(this.q1.shift());
    }

    // The last item in q1 is our stack's top
    const poppedItem = this.q1.shift();

    // Swap q1 and q2
    [this.q1, this.q2] = [this.q2, this.q1];

    return poppedItem;
  }

  // O(n) operation
  peek() {
    if (this.isEmpty()) {
      return undefined;
    }

    let lastItem;
    while (this.q1.length > 0) {
      lastItem = this.q1.shift();
      this.q2.push(lastItem);
    }

    [this.q1, this.q2] = [this.q2, this.q1];

    return lastItem;
  }

  isEmpty() {
    return this.q1.length === 0;
  }

  size() {
    return this.q1.length;
  }
}
```

### How This Works:
1. **Push**: Simply add to the main queue (q1)
2. **Pop**: 
   - Move all elements except the last from q1 to q2
   - The last element is the one we want (LIFO)
   - Swap the queues so q1 becomes the main queue again

## Approach 2: Using Two Queues (Pop Efficient)

This method makes `pop` efficient (O(1)) while `push` becomes O(n).

```javascript
class StackUsingQueues {
  constructor() {
    this.q1 = []; // Main queue
    this.q2 = []; // Temporary queue
  }

  // O(n) operation
  push(item) {
    // Add to empty q2
    this.q2.push(item);
    
    // Move all items from q1 to q2
    while (this.q1.length > 0) {
      this.q2.push(this.q1.shift());
    }
    
    // Swap q1 and q2
    [this.q1, this.q2] = [this.q2, this.q1];
  }

  // O(1) operation
  pop() {
    if (this.isEmpty()) {
      return undefined;
    }
    return this.q1.shift();
  }

  // O(1) operation
  peek() {
    if (this.isEmpty()) {
      return undefined;
    }
    return this.q1[0];
  }

  isEmpty() {
    return this.q1.length === 0;
  }

  size() {
    return this.q1.length;
  }
}
```

### How This Works:
1. **Push**: 
   - Add new item to empty q2
   - Move all items from q1 to q2 (puts new item at front)
   - Swap the queues
2. **Pop**: Simply remove from front of q1 (which is the last pushed item)

## Approach 3: Using One Queue

We can implement it with just one queue by rotating elements during push.

```javascript
class StackUsingOneQueue {
  constructor() {
    this.queue = [];
  }

  // O(n) operation
  push(item) {
    this.queue.push(item);
    // Rotate the queue to put the new item at front
    for (let i = 0; i < this.queue.length - 1; i++) {
      this.queue.push(this.queue.shift());
    }
  }

  // O(1) operation
  pop() {
    if (this.isEmpty()) {
      return undefined;
    }
    return this.queue.shift();
  }

  // O(1) operation
  peek() {
    if (this.isEmpty()) {
      return undefined;
    }
    return this.queue[0];
  }

  isEmpty() {
    return this.queue.length === 0;
  }

  size() {
    return this.queue.length;
  }
}
```

### How This Works:
1. **Push**: 
   - Add new item to the queue
   - Rotate all previous items to the back (puts new item at front)
2. **Pop**: Remove from front (which is the last pushed item)

## Time Complexity Comparison

| Operation | Two Queues (Push Efficient) | Two Queues (Pop Efficient) | One Queue |
|-----------|----------------------------|---------------------------|----------|
| push()    | O(1)                       | O(n)                      | O(n)     |
| pop()     | O(n)                       | O(1)                      | O(1)     |
| peek()    | O(n)                       | O(1)                      | O(1)     |
| isEmpty() | O(1)                       | O(1)                      | O(1)     |

## Which Approach to Choose?

1. **If pushes are more frequent**: Use the push-efficient approach
2. **If pops are more frequent**: Use the pop-efficient approach
3. **If memory is a concern**: Use the single queue approach

## Practical Example

Let's see how the push-efficient approach works step by step:

```javascript
const stack = new StackUsingQueues();
stack.push(10); // q1: [10], q2: []
stack.push(20); // q1: [10, 20], q2: []
stack.push(30); // q1: [10, 20, 30], q2: []

stack.pop(); // Steps:
// Move 10 and 20 to q2: q1: [30], q2: [10, 20]
// Pop 30
// Swap q1 and q2: q1: [10, 20], q2: []
// Return 30
```

## Key Takeaways

1. **Trade-offs**: You can make either push or pop efficient, but not both
2. **Queue Behavior**: Remember queues are FIFO, so we need to manipulate them to get LIFO behavior
3. **Practice**: Try implementing both approaches to fully understand the differences

This exercise helps you understand:
- The fundamental differences between stacks and queues
- How to manipulate one data structure to behave like another
- The importance of time complexity in algorithm design



# Implementing a Queue Using Stacks

Since you're a beginner, I'll explain this step-by-step with simple examples. A queue is First-In-First-Out (FIFO), while a stack is Last-In-First-Out (LIFO). We need to make LIFO behave like FIFO using stacks.

## Approach 1: Using Two Stacks (Enqueue Efficient)

This method makes `enqueue` efficient (O(1)) while `dequeue` becomes O(n) in worst case.

```javascript
class QueueUsingStacks {
  constructor() {
    this.stack1 = []; // Main stack for enqueue
    this.stack2 = []; // Temporary stack for dequeue
  }

  // O(1) operation - just push to stack1
  enqueue(item) {
    this.stack1.push(item);
  }

  // O(n) in worst case
  dequeue() {
    if (this.isEmpty()) {
      return undefined;
    }

    // If stack2 is empty, move all elements from stack1 to stack2
    if (this.stack2.length === 0) {
      while (this.stack1.length > 0) {
        this.stack2.push(this.stack1.pop());
      }
    }

    // Pop from stack2 (which is the front of the queue)
    return this.stack2.pop();
  }

  // O(n) in worst case
  peek() {
    if (this.isEmpty()) {
      return undefined;
    }

    if (this.stack2.length === 0) {
      while (this.stack1.length > 0) {
        this.stack2.push(this.stack1.pop());
      }
    }

    return this.stack2[this.stack2.length - 1];
  }

  isEmpty() {
    return this.stack1.length === 0 && this.stack2.length === 0;
  }

  size() {
    return this.stack1.length + this.stack2.length;
  }
}
```

### How This Works:
1. **Enqueue**: Simply push to stack1 (O(1))
2. **Dequeue**:
   - If stack2 is empty, pop all from stack1 and push to stack2 (reverses order)
   - Then pop from stack2 (which is the oldest item)
3. **Peek**: Similar to dequeue but without removing

## Approach 2: Using Two Stacks (Dequeue Efficient)

This method makes `dequeue` efficient (O(1)) while `enqueue` becomes O(n).

```javascript
class QueueUsingStacks {
  constructor() {
    this.stack1 = []; // Main stack
    this.stack2 = []; // Temporary stack
  }

  // O(n) operation
  enqueue(item) {
    // Move all elements from stack1 to stack2
    while (this.stack1.length > 0) {
      this.stack2.push(this.stack1.pop());
    }

    // Push new item to stack1
    this.stack1.push(item);

    // Move all elements back from stack2 to stack1
    while (this.stack2.length > 0) {
      this.stack1.push(this.stack2.pop());
    }
  }

  // O(1) operation
  dequeue() {
    if (this.isEmpty()) {
      return undefined;
    }
    return this.stack1.pop();
  }

  // O(1) operation
  peek() {
    if (this.isEmpty()) {
      return undefined;
    }
    return this.stack1[this.stack1.length - 1];
  }

  isEmpty() {
    return this.stack1.length === 0;
  }

  size() {
    return this.stack1.length;
  }
}
```

### How This Works:
1. **Enqueue**:
   - Move all existing items to stack2
   - Add new item to stack1
   - Move all items back from stack2 (puts new item at bottom)
2. **Dequeue**: Simply pop from stack1 (always the oldest item)

## Approach 3: Using Function Call Stack (Recursion)

We can implement a queue using just one stack and recursion (using the call stack as the second stack).

```javascript
class QueueUsingOneStack {
  constructor() {
    this.stack = [];
  }

  // O(1) operation
  enqueue(item) {
    this.stack.push(item);
  }

  // O(n) operation using recursion
  dequeue() {
    if (this.stack.length === 0) {
      return undefined;
    }
    if (this.stack.length === 1) {
      return this.stack.pop();
    }
    
    const item = this.stack.pop();
    const result = this.dequeue();
    this.stack.push(item);
    return result;
  }

  // O(n) operation using recursion
  peek() {
    if (this.stack.length === 0) {
      return undefined;
    }
    if (this.stack.length === 1) {
      return this.stack[this.stack.length - 1];
    }
    
    const item = this.stack.pop();
    const result = this.peek();
    this.stack.push(item);
    return result;
  }

  isEmpty() {
    return this.stack.length === 0;
  }

  size() {
    return this.stack.length;
  }
}
```

### How This Works:
1. **Enqueue**: Simple push to stack
2. **Dequeue**:
   - Uses recursion to reach the bottom of the stack
   - Returns the bottom element (oldest)
   - Pushes all other elements back
3. **Peek**: Similar to dequeue but without removing

## Time Complexity Comparison

| Operation | Two Stacks (Enqueue Efficient) | Two Stacks (Dequeue Efficient) | One Stack (Recursive) |
|-----------|-------------------------------|-------------------------------|----------------------|
| enqueue() | O(1)                          | O(n)                          | O(1)                 |
| dequeue() | O(n) (amortized O(1))         | O(1)                          | O(n)                 |
| peek()    | O(n) (amortized O(1))         | O(1)                          | O(n)                 |
| isEmpty() | O(1)                          | O(1)                          | O(1)                 |

## Which Approach to Choose?

1. **If enqueues are more frequent**: Use the enqueue-efficient approach
2. **If dequeues are more frequent**: Use the dequeue-efficient approach
3. **If you want to understand recursion**: Try the one-stack approach

## Practical Example

Let's see how the enqueue-efficient approach works:

```javascript
const queue = new QueueUsingStacks();
queue.enqueue(10); // stack1: [10], stack2: []
queue.enqueue(20); // stack1: [10, 20], stack2: []
queue.enqueue(30); // stack1: [10, 20, 30], stack2: []

queue.dequeue(); // Steps:
// stack2 is empty, so move all to stack2:
// stack1: [], stack2: [30, 20, 10]
// pop from stack2: returns 10
// stack1: [], stack2: [30, 20]

queue.peek(); // Returns 20 (top of stack2)
```

## Key Takeaways

1. **Trade-offs**: You can optimize for either enqueue or dequeue, but not both
2. **Stack Behavior**: Remember stacks are LIFO, so we need to reverse them to get FIFO behavior
3. **Amortized Cost**: While dequeue is O(n) in worst case, it's O(1) amortized if we don't always empty stack2

This exercise helps you understand:
- The relationship between stacks and queues
- How to use one data structure to simulate another
- The importance of operation costs in data structure design





# What is a Priority Queue?

A **Priority Queue** is an **abstract data structure** similar to a queue, **but each element has a priority**. Elements are **removed based on priority, not insertion order**.

✅ **Higher priority elements are dequeued before lower priority elements**, regardless of when they were inserted.

---

### 🚦 Comparison with Other Structures:

|Structure|Removal Order|
|---|---|
|**Queue**|FIFO (First-In, First-Out)|
|**Stack**|LIFO (Last-In, First-Out)|
|**Priority Queue**|Based on **priority** (not insertion order)|

---

## 🚀 Real-World Examples:

✅ Emergency room (critical patients treated first)  
✅ Task scheduling in OS (higher priority processes run first)  
✅ Algorithms like Dijkstra’s shortest path, Huffman coding.

---

## 🚀 Types of Priority Queues:

- **Min Priority Queue:** Lower priority value = higher priority (e.g., priority `1` is higher than `5`).
    
- **Max Priority Queue:** Higher priority value = higher priority (e.g., priority `5` is higher than `1`).
    

---

## 🚀  Implementation using queue

##           🚀 Approach

Queues are **FIFO**, but Priority Queues need **priority-based removal**.

Since we cannot directly leverage the queue’s nature for priority, we will:  
✅ **Maintain the queue in sorted order upon insertion** based on priority:

- **Lower priority number = higher priority** (Min-Priority Queue).  
    ✅ On `dequeue`, simply `shift()` to remove the front element (highest priority).  
    ✅ On `peek`, return `queue[0]`.
    

**⚠️ Note:** This results in `O(n)` insertion time and `O(1)` removal, which is acceptable for understanding but not efficient for large-scale use (use heaps in real systems).

---

## 🚀 JavaScript Implementation

```javascript
class PriorityQueueUsingQueue {
    constructor() {
        this.queue = []; // Array used as a queue
    }

    // Insert an element with its priority
    enqueue(value, priority) {
        const newItem = { value, priority };
        let added = false;

        // Insert at the correct position to maintain priority order
        for (let i = 0; i < this.queue.length; i++) {
            if (newItem.priority < this.queue[i].priority) {
                this.queue.splice(i, 0, newItem);
                added = true;
                break;
            }
        }

        // If the new item has the lowest priority, push it to the end
        if (!added) {
            this.queue.push(newItem);
        }
    }

    // Remove and return the element with the highest priority (front)
    dequeue() {
        if (this.isEmpty()) {
            console.log("Queue is empty.");
            return null;
        }
        return this.queue.shift();
    }

    // Peek at the element with the highest priority
    peek() {
        if (this.isEmpty()) {
            console.log("Queue is empty.");
            return null;
        }
        return this.queue[0];
    }

    // Check if the queue is empty
    isEmpty() {
        return this.queue.length === 0;
    }

    // Utility to display the current queue
    print() {
        console.log(this.queue.map(item => `${item.value} (Priority: ${item.priority})`).join(" -> "));
    }
}

// Example usage:
const pq = new PriorityQueueUsingQueue();
pq.enqueue("Eat", 2);
pq.enqueue("Code", 1);
pq.enqueue("Sleep", 3);
pq.enqueue("Walk", 2);

pq.print(); // Expected: Code (1) -> Eat (2) -> Walk (2) -> Sleep (3)

console.log(pq.dequeue()); // { value: 'Code', priority: 1 }
pq.print(); // Eat (2) -> Walk (2) -> Sleep (3)

console.log(pq.peek()); // { value: 'Eat', priority: 2 }
```

---

## 🚀 Summary:

✅ This Priority Queue using a Queue:

- Inserts in sorted order (`O(n)`) to maintain priority.
    
- Dequeues the highest priority element efficiently (`O(1)`).
    
- Good for **practicing Priority Queue logic while reinforcing queue operations**.
    


## 🚀 Why Use Priority Queue?

✅ Allows **efficient management of prioritized tasks**.  
✅ Core in **graph algorithms, CPU scheduling, simulations, event management**.  
✅ Ensures **predictable and structured task handling** in projects and system design.

---

## 🚀 Summary:

✅ A **Priority Queue** prioritizes element removal based on their priority, not insertion order.  
✅ Efficiently implemented using **binary heaps for O(log n) operations**.  
✅ Essential for **interview DSA, system design, and real projects**.

---

If you want:  
✅ A **visual diagram illustrating how enqueue and dequeue work step-by-step** in this implementation,  
✅ **Practice problems** using Priority Queues for LeetCode,  
✅ A **Max-Heap Priority Queue implementation** for comparison and mastery,




