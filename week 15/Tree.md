# 🚀Trees in Data Structures 

A tree is a hierarchical, non-linear data structure that consists of nodes connected by edges. Unlike linear data structures like arrays and linked lists, trees provide a way to organize data hierarchically, which makes them efficient for many operations.

## Basic Terminology



```
        A (Root)
       /   \
      B     C
     / \     \
    D   E     F
         \
          G (Leaf)
```

### Terminology Explained with This Example:

1. **Node**: Each letter (A, B, C, etc.) represents a node containing data
2. **Root**: Node A (the topmost node with no parent)
3. **Parent**:
   - A is parent of B and C
   - B is parent of D and E
   - C is parent of F
   - E is parent of G
4. **Child**:
   - B and C are children of A
   - D and E are children of B
   - F is child of C
   - G is child of E
5. **Siblings**:
   - B and C are siblings (both children of A)
   - D and E are siblings
6. **Leaf/External Node**: D, F, G (nodes with no children)
7. **Internal Node**: A, B, C, E (nodes with at least one child)
8. **Edge**: The lines connecting nodes (A-B, A-C, B-D, etc.)
9. **Depth**:
   - A: depth 0
   - B, C: depth 1
   - D, E, F: depth 2
   - G: depth 3
10. **Height**:
    - G: height 0
    - D, F: height 1
    - E: height 2
    - B, C: height 3
    - A: height 4
11. **Degree**:
    - A: degree 2 (has 2 children)
    - B: degree 2
    - C: degree 1
    - E: degree 1
    - D, F, G: degree 0
12. **Subtree**:
    - The subtree rooted at B is:
      ```
        B
       / \
      D   E
           \
            G
      ```
13. **Ancestors**:
    - Ancestors of G: E, B, A
14. **Descendants**:
    - Descendants of B: D, E, G



## Tree Implementation in JavaScript

Here's a basic implementation of a tree node in JavaScript:

```javascript
class TreeNode {
  constructor(data) {
    this.data = data;
    this.children = [];
  }

  addChild(childNode) {
    this.children.push(childNode);
  }
}

// Creating a simple tree
const root = new TreeNode('Root');
const child1 = new TreeNode('Child 1');
const child2 = new TreeNode('Child 2');
const grandchild1 = new TreeNode('Grandchild 1');

root.addChild(child1);
root.addChild(child2);
child1.addChild(grandchild1);
```

## Types of Trees

### 1. Binary Tree
- Each node has at most 2 children (left and right)
- Implementation:
  ```javascript
  class BinaryTreeNode {
    constructor(data) {
      this.data = data;
      this.left = null;
      this.right = null;
    }
  }
  ```

### 2. Binary Search Tree (BST)
- Left subtree contains only nodes with values less than the parent
- Right subtree contains only nodes with values greater than the parent
- No duplicate nodes
- Efficient for search operations (O(log n) average case)

### 3. AVL Tree
- Self-balancing BST
- Maintains balance factor (height difference between left and right subtrees) of -1, 0, or 1
- Rotations are performed to maintain balance

### 4. Red-Black Tree
- Another self-balancing BST
- Nodes are colored red or black with specific rules to maintain balance
- Used in many language libraries (like C++ STL)

### 5. B-Tree
- Generalization of BST where each node can have more than two children
- Used in databases and file systems for efficient disk access

### 6. Trie (Prefix Tree)
- Used for storing strings where each node represents a character
- Efficient for prefix searches and autocomplete systems

### 7. Heap
- Complete binary tree where parent nodes are ordered relative to children
- Min-Heap: Parent ≤ Children
- Max-Heap: Parent ≥ Children
- Used in priority queues and heap sort

## Tree Traversals

1. **Depth-First Search (DFS)**
   - Pre-order: Root → Left → Right
   - In-order: Left → Root → Right (gives sorted order in BST)
   - Post-order: Left → Right → Root

2. **Breadth-First Search (BFS)**
   - Level-order traversal (uses a queue)

```javascript
// DFS Pre-order implementation
function preOrder(node) {
  if (!node) return;
  console.log(node.data); // Process node
  preOrder(node.left);
  preOrder(node.right);
}

// BFS implementation
function levelOrder(root) {
  if (!root) return;
  const queue = [root];
  while (queue.length) {
    const node = queue.shift();
    console.log(node.data); // Process node
    if (node.left) queue.push(node.left);
    if (node.right) queue.push(node.right);
  }
}
```

## Use Cases of Trees

1. **File Systems**: Directory structure is naturally represented as a tree
2. **DOM**: The HTML Document Object Model is a tree structure
3. **Databases**: Indexing structures like B-trees and B+ trees(in mongodb ).
4. **Networking**: Routing tables and decision trees
5. **Artificial Intelligence**: Decision trees for machine learning
6. **Compilers**: Abstract syntax trees represent program structure
7. **Autocomplete**: Tries for efficient prefix searches
8. **Game Development**: Game decision trees and scene graphs
9. **Blockchain**: Merkle trees for efficient verification
10. **Compression**: Huffman coding trees

## Advantages of Trees

1. Efficient for hierarchical data representation
2. Provide moderate access/search (better than linear structures)
3. Provide moderate insertion/deletion (better than arrays)
4. Flexible size (unlike arrays)
5. Can maintain order (in BSTs)
6. Useful for representing sorted lists and priority queues

## Disadvantages of Trees

1. More complex than linear structures
2. Performance can degrade to O(n) if not balanced
3. Require additional memory for pointers/references
4. Some operations require recursive implementations which can be less efficient

Trees are fundamental in computer science and understanding them is crucial for solving many complex problems efficiently. They provide the foundation for more advanced data structures and algorithms used in virtually all areas of software development.


# 🚀Types of Binary Trees

Binary trees are hierarchical data structures where each node has at most two children, referred to as the left child and right child. There are several specialized types of binary trees, each with unique properties and use cases. Let's explore them in depth.

## 1. Full (Strict) Binary Tree
A binary tree is **full** if every node has either 0 or 2 children (no nodes have only 1 child).

**Properties:**
- Number of leaf nodes = Number of internal nodes + 1
- Maximum number of nodes at level `l` is 2^l
- Total nodes in a full binary tree of height `h`: 2^(h+1) - 1

**Example:**
```
      A
    /   \
   B     C
  / \   / \
 D   E F   G
```

## 2. Complete Binary Tree
A binary tree is **complete** if all levels are completely filled except possibly the last level, which must be filled from left to right.

**Properties:**
- Height of complete binary tree with n nodes: ⌊log₂n⌋
- Efficient array representation (no gaps in storage)
- Used in binary heaps

**Example:**
```
      A
    /   \
   B     C
  / \   /
 D   E F
```

## 3. Perfect Binary Tree
A binary tree is **perfect** if all internal nodes have exactly two children and all leaf nodes are at the same level.

**Properties:**
- Number of nodes = 2^(h+1) - 1 where h is height
- Number of leaf nodes = 2^h
- All perfect binary trees are complete and full

**Example:**
```
      A
    /   \
   B     C
  / \   / \
 D   E F   G
```

## 4. Balanced Binary Tree
A binary tree is **balanced** if the height of the left and right subtrees of every node differ by no more than 1.

**Properties:**
- Ensures O(log n) time for search, insert, delete operations
- AVL trees and Red-Black trees are self-balancing variants

**Example:**
```
      A
    /   \
   B     C
  /     / \
 D     E   F
```

## 5. Degenerate (Pathological) Binary Tree
A binary tree is **degenerate** if each parent node has only one child, effectively becoming a linked list.

**Properties:**
- Worst case performance (O(n) for operations)
- Can be left-skewed or right-skewed

**Example (left-skewed):**
```
      A
     /
    B
   /
  C
 /
D
```

## 6. Binary Search Tree (BST)
A binary tree where for each node:
- All nodes in left subtree have values less than the node's value
- All nodes in right subtree have values greater than the node's value

**Properties:**
- In-order traversal yields sorted sequence
- Average case O(log n) for search operations

**Example:**
```
      4
    /   \
   2     6
  / \   / \
 1   3 5   7
```

## 7. AVL Tree
A self-balancing BST where the difference between heights of left and right subtrees cannot be more than 1 for all nodes.

**Properties:**
- Guarantees O(log n) search time
- Uses rotations to maintain balance after insertions/deletions

## 8. Red-Black Tree
Another self-balancing BST with additional color attributes (red/black) that maintain balance through color rules.

**Properties:**
- Root is always black
- No two adjacent red nodes
- Every path from node to descendant leaf has same number of black nodes

## 9. Threaded Binary Tree
A binary tree where null pointers are replaced with threads (pointers) to other nodes for efficient traversal.

**Types:**
- Single-threaded: Only null right pointers are threaded
- Double-threaded: Both left and right null pointers are threaded

## 10. B-Tree (Not strictly binary)
While not a binary tree (nodes can have more than two children), B-trees are important variants used in database systems.

## 11. Heap (Binary Heap)
A complete binary tree that satisfies the heap property:
- Max-heap: Parent ≥ children
- Min-heap: Parent ≤ children

**Applications:**
- Priority queues
- Heap sort algorithm

## Specialized Binary Trees

### Expression Tree
Represents mathematical expressions where:
- Leaf nodes are operands
- Internal nodes are operators

**Example (for 3 + 4 * 5):**
```
     +
    / \
   3   *
      / \
     4   5
```

### Tournament Tree
Used to track winners of matches in a tournament structure.

### Huffman Tree
Used in data compression algorithms where:
- Characters are represented by binary codes
- Frequent characters have shorter codes

Each type of binary tree serves specific purposes in computer science, from efficient searching and sorting to memory optimization and data compression. Understanding their properties helps in selecting the right structure for a given problem.


# 🚀Binary Search Tree (BST) 

A Binary Search Tree (BST) is a node-based binary tree data structure where each node has at most two children referred to as the left child and the right child.

## BST Properties

- **Left Subtree**: Contains nodes with values less than the parent node
- **Right Subtree**: Contains nodes with values greater than the parent node
- **No Duplicate Nodes**: Typically, BSTs don't contain duplicate values

## JavaScript Implementation

```javascript
class Node {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

class BinarySearchTree {
  constructor() {
    this.root = null;
  }

  // Insert a value
  insert(value) {
    const newNode = new Node(value);
    
    if (!this.root) {
      this.root = newNode;
      return this;
    }
    
    let current = this.root;
    while (true) {
      if (value === current.value) return undefined; // or handle duplicates
      
      if (value < current.value) {
        if (!current.left) {
          current.left = newNode;
          return this;
        }
        current = current.left;
      } else {
        if (!current.right) {
          current.right = newNode;
          return this;
        }
        current = current.right;
      }
    }
  }

  // Find a value
  find(value) {
    if (!this.root) return false;
    
    let current = this.root;
    while (current) {
      if (value === current.value) return current;
      
      if (value < current.value) {
        current = current.left;
      } else {
        current = current.right;
      }
    }
    return false;
  }

  // Other operations would include:
  // - remove()
  // - BFS/DFS traversals
  // - etc.
}
```

## Applications of BSTs

1. **Database Indexing**: Many databases use BST variants (like B-trees) for indexing
2. **File Systems**: Directory structures often use tree representations
3. **Routing Tables**: In networking for IP routing
4. **Auto-completion**: Search suggestions can use tries (a BST variant)
5. **Game Development**: For spatial partitioning
6. **Compression Algorithms**: Huffman coding uses binary trees

## Advantages

1. **Efficient Searching**: O(log n) average case for search, insert, delete
2. **Ordered Structure**: Maintains elements in sorted order
3. **Flexible Size**: Can grow and shrink dynamically
4. **Efficient Range Queries**: Can find all elements in a range efficiently
5. **Successor/Predecessor**: Easy to find next higher/lower element

## Disadvantages

1. **Performance Degradation**: Can degrade to O(n) in worst case (unbalanced tree)
2. **Memory Overhead**: Each node requires additional memory for pointers
3. **Complex Balancing**: Requires additional logic to maintain balance (AVL, Red-Black trees)
4. **Not Cache-Friendly**: Nodes may be scattered in memory

## Common Operations and Complexities

| Operation      | Average Case | Worst Case |
|---------------|-------------|------------|
| Insert        | O(log n)    | O(n)       |
| Search        | O(log n)    | O(n)       |
| Delete        | O(log n)    | O(n)       |
| Find Min/Max  | O(log n)    | O(n)       |
| Traversal     | O(n)        | O(n)       |
| Space         | O(n)        | O(n)       |

*Note: The worst case occurs when the tree becomes a linear chain (completely unbalanced). Self-balancing BSTs like AVL or Red-Black trees guarantee O(log n) performance for all operations.*

## Balancing BSTs

To maintain O(log n) performance, BSTs often implement balancing techniques:
- **AVL Trees**: Strict balance condition
- **Red-Black Trees**: More relaxed balance than AVL
- **B-Trees**: For disk-based storage systems
- **Splay Trees**: Self-adjusting based on access patterns

# 🚀Tree Traversal Techniques in BST

Tree traversal refers to the process of visiting (checking or updating) each node in a tree data structure exactly once. In BSTs, there are several important traversal techniques that serve different purposes.

## Types of Tree Traversals

There are two main categories of tree traversals:
1. **Depth-First Traversal (DFS)**
   - Inorder (Left, Root, Right)
   - Preorder (Root, Left, Right)
   - Postorder (Left, Right, Root)
2. **Breadth-First Traversal (BFS)**
   - Level Order Traversal

## 1. Depth-First Traversals

### a. Inorder Traversal

**Order**: Left subtree → Root → Right subtree  
**Result**: Nodes are visited in ascending order (for BST)  
**Applications**: Getting nodes in sorted order, expression trees

```javascript
// Recursive implementation
inOrderTraversal(node = this.root) {
  if (node !== null) {
    this.inOrderTraversal(node.left);
    console.log(node.value); // Process the node
    this.inOrderTraversal(node.right);
  }
}

// Iterative implementation using stack
inOrderIterative() {
  const stack = [];
  let current = this.root;
  
  while (current !== null || stack.length > 0) {
    // Reach the leftmost node
    while (current !== null) {
      stack.push(current);
      current = current.left;
    }
    
    current = stack.pop();
    console.log(current.value); // Process the node
    current = current.right;
  }
}
```

### b. Preorder Traversal

**Order**: Root → Left subtree → Right subtree  
**Applications**: Creating a copy of the tree, prefix notation of expression trees

```javascript
// Recursive implementation
preOrderTraversal(node = this.root) {
  if (node !== null) {
    console.log(node.value); // Process the node
    this.preOrderTraversal(node.left);
    this.preOrderTraversal(node.right);
  }
}

// Iterative implementation using stack
preOrderIterative() {
  if (this.root === null) return;
  
  const stack = [this.root];
  
  while (stack.length > 0) {
    const current = stack.pop();
    console.log(current.value); // Process the node
    
    // Push right first so left is processed first
    if (current.right !== null) stack.push(current.right);
    if (current.left !== null) stack.push(current.left);
  }
}
```

### c. Postorder Traversal

**Order**: Left subtree → Right subtree → Root  
**Applications**: Deleting the tree, postfix notation of expression trees

```javascript
// Recursive implementation
postOrderTraversal(node = this.root) {
  if (node !== null) {
    this.postOrderTraversal(node.left);
    this.postOrderTraversal(node.right);
    console.log(node.value); // Process the node
  }
}

// Iterative implementation using two stacks
postOrderIterative() {
  if (this.root === null) return;
  
  const stack1 = [this.root];
  const stack2 = [];
  
  while (stack1.length > 0) {
    const current = stack1.pop();
    stack2.push(current);
    
    if (current.left !== null) stack1.push(current.left);
    if (current.right !== null) stack1.push(current.right);
  }
  
  while (stack2.length > 0) {
    console.log(stack2.pop().value); // Process the node
  }
}
```

## 2. Breadth-First Traversal (Level Order)

**Order**: Nodes are visited level by level from top to bottom and left to right within each level  
**Applications**: Finding the shortest path (in unweighted trees), printing tree structure

```javascript
levelOrderTraversal() {
  if (this.root === null) return;
  
  const queue = [this.root];
  
  while (queue.length > 0) {
    const current = queue.shift();
    console.log(current.value); // Process the node
    
    if (current.left !== null) queue.push(current.left);
    if (current.right !== null) queue.push(current.right);
  }
}
```

## Time and Space Complexity

| Traversal Method | Time Complexity | Space Complexity (Worst) |
|-----------------|----------------|--------------------------|
| Inorder         | O(n)           | O(h) [h = tree height]   |
| Preorder        | O(n)           | O(h)                     |
| Postorder       | O(n)           | O(h)                     |
| Level Order     | O(n)           | O(w) [w = max width]     |

*Notes:*
- For recursive implementations, space complexity is O(h) due to the call stack
- For a balanced tree, h = O(log n)
- For a skewed tree, h = O(n)
- Level order uses O(n) space in worst case (complete binary tree)

## Practical Example

```javascript
class BST {
  // ... (previous BST implementation from earlier)

  // All traversal methods would be added here
}

// Usage
const bst = new BST();
bst.insert(10);
bst.insert(5);
bst.insert(15);
bst.insert(3);
bst.insert(7);
bst.insert(12);
bst.insert(18);

console.log("Inorder:");
bst.inOrderTraversal(); // 3, 5, 7, 10, 12, 15, 18

console.log("Preorder:");
bst.preOrderTraversal(); // 10, 5, 3, 7, 15, 12, 18

console.log("Postorder:");
bst.postOrderTraversal(); // 3, 7, 5, 12, 18, 15, 10

console.log("Level Order:");
bst.levelOrderTraversal(); // 10, 5, 15, 3, 7, 12, 18
```

Each traversal serves different purposes and choosing the right one depends on your specific use case. Inorder is particularly useful with BSTs as it gives nodes in sorted order.

# 🚀BFS search Visual explanation

![[Pasted image 20250726000743.png]]
The output for the above tree for BFS will be 10, 5 ,15 ,  3 and 7;

## Traversal Approach

![[Pasted image 20250726000922.png]]
![[Pasted image 20250726001047.png]]

### Binary search tree with all traversal techniques 

```javascript
class Node{
    constructor(value){
        this.value = value;
        this.left = null;
        this.right = null;
    }
}

class BinarySTree{
    constructor(){
        this.root = null;
        this.size = 0;
    }
    
    insert(value){
        let node = new Node(value);
        if(this.root == null){
            this.root = node;
            this.size++;
        } else {
            this.insertNode(this.root,node);
        }
    }
    
    insertNode(root,node){
        if(node.value<root.value){
            if(root.left == null){
                root.left = node;
                 this.size++;
            } else {
                this.insertNode(root.left,node);
            }
        } else {
            if(root.right == null){
                root.right = node;
                 this.size++;
            } else {
                this.insertNode(root.right, node);
            }
        }
    }
    
    preOrder(node= this.root){
        if(node == null){
            return;
        }
        
        console.log(node.value);
        this.preOrder(node.left);
        this.preOrder(node.right);
        
    }
    
    inOrder(node = this.root){
        if(node == null){
            return;
        }
        this.inOrder(node.left);
        console.log(node.value);
        this.inOrder(node.right);
    }
    
    postOrder(node = this.root){
        if(node == null) return;
        
        this.postOrder(node.left);
        this.postOrder(node.right);
        console.log(node.value);
    }
    
    levelOrder(){
        let queue  = [];
        queue.push(this.root);
        while(queue.length!=0){
            let elem = queue.shift();
            console.log(elem.value);
            if(elem.left!=null) queue.push(elem.left);
            if(elem.right!=null) queue.push(elem.right);
        }
    }
    
    
    
    isEmpty(){
        return this.root == null;
    }
    
    getSize(){
        return this.size;
    }
}


let bt = new BinarySTree();
let arr = [6,5,2,7,3,8,1,9];
for(let item of arr){
    bt.insert(item);
}
// console.log(bt.getSize());
bt.levelOrder();


```