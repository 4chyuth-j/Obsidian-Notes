# Hash Tables in JavaScript

A hash table (also called a hash map) is a fundamental data structure that implements an associative array, a structure that can map keys to values. In JavaScript, objects and Maps are essentially hash table implementations, but understanding how they work under the hood is valuable.

## How Hash Tables Work

At its core, a hash table uses:
1. A **hash function** to convert keys into array indices
2. An **array** to store the data
3. A **collision resolution** strategy for when multiple keys hash to the same index

### Basic Mechanism

1. When you add a key-value pair, the hash function computes an index from the key
2. The value is stored at that index in the underlying array
3. When you retrieve by key, the same hash function locates the value

## Applications of Hash Tables

Hash tables are used in many scenarios because of their average O(1) time complexity for insertions, deletions, and lookups:

1. **Caching systems**: Memoization, browser caching
2. **Database indexing**: Fast record lookup
3. **Counters**: Frequency analysis, word counts
4. **Unique item tracking**: Removing duplicates
5. **Object property storage**: How JavaScript objects work internally
6. **Graph algorithms**: Adjacency list representations

## Advantages

1. **Fast operations**: Average case O(1) for insert, delete, search
2. **Flexible keys**: Can use any hashable data type as key
3. **Efficient memory usage**: Only allocates what's needed

## Disadvantages

1. **Hash collisions**: Can degrade performance to O(n) in worst case
2. **No ordered iteration**: Keys are not stored in insertion order (though JavaScript's Map preserves order)
3. **Space overhead**: Typically uses more memory than arrays
4. **Hash function quality**: Performance depends on good hash function

## Manual Implementation in JavaScript

Here's a basic implementation of a hash table in JavaScript:

```javascript
class HashTable {
  constructor(size = 53) {
    this.keyMap = new Array(size);
  }

  // Basic hash function (not production quality)
  _hash(key) {
    let total = 0;
    const WEIRD_PRIME = 31;
    for (let i = 0; i < Math.min(key.length, 100); i++) {
      const char = key[i];
      const value = char.charCodeAt(0) - 96;
      total = (total * WEIRD_PRIME + value) % this.keyMap.length;
    }
    return total;
  }

  // Set a key-value pair
  set(key, value) {
    const index = this._hash(key);
    if (!this.keyMap[index]) {
      this.keyMap[index] = [];
    }
    // Check if key already exists, if so update it
    for (let i = 0; i < this.keyMap[index].length; i++) {
      if (this.keyMap[index][i][0] === key) {
        this.keyMap[index][i][1] = value;
        return;
      }
    }
    this.keyMap[index].push([key, value]);
  }

  // Get a value by key
  get(key) {
    const index = this._hash(key);
    if (this.keyMap[index]) {
      for (let item of this.keyMap[index]) {
        if (item[0] === key) {
          return item[1];
        }
      }
    }
    return undefined;
  }

  // Get all keys
  keys() {
    const keysArr = [];
    for (let i = 0; i < this.keyMap.length; i++) {
      if (this.keyMap[i]) {
        for (let item of this.keyMap[i]) {
          if (!keysArr.includes(item[0])) {
            keysArr.push(item[0]);
          }
        }
      }
    }
    return keysArr;
  }

  // Get all values
  values() {
    const valuesArr = [];
    for (let i = 0; i < this.keyMap.length; i++) {
      if (this.keyMap[i]) {
        for (let item of this.keyMap[i]) {
          if (!valuesArr.includes(item[1])) {
            valuesArr.push(item[1]);
          }
        }
      }
    }
    return valuesArr;
  }
}
```

### Usage Example

```javascript
const ht = new HashTable(17);
ht.set("maroon", "#800000");
ht.set("yellow", "#FFFF00");
ht.set("olive", "#808000");
ht.set("salmon", "#FA8072");
ht.set("lightcoral", "#F08080");

console.log(ht.get("yellow")); // "#FFFF00"
console.log(ht.keys()); // ["maroon", "yellow", "olive", "salmon", "lightcoral"]
console.log(ht.values()); // ["#800000", "#FFFF00", "#808000", "#FA8072", "#F08080"]
```

## Collision Resolution

The above implementation uses **separate chaining** (storing multiple key-value pairs at the same index using an array). Another common approach is **linear probing** (finding the next empty slot when a collision occurs).

## JavaScript's Built-in Hash Tables

1. **Objects**: The most basic hash table implementation in JS
   ```javascript
   const obj = {};
   obj['key'] = 'value';
   ```

2. **Map**: More sophisticated with some advantages over plain objects
   ```javascript
   const map = new Map();
   map.set('key', 'value');
   ```

Key differences between Objects and Maps:
- Maps preserve insertion order, objects don't (in modern JS, objects do maintain insertion order)
- Maps allow any data type as keys, objects only allow strings/Symbols
- Maps have better performance for frequent additions/removals

## Real-world Considerations

1. **Dynamic resizing**: A production hash table should resize when load factor (items/slots) gets too high
2. **Better hash functions**: The simple one shown here has limitations
3. **Security**: Some hash functions are vulnerable to DoS attacks via deliberate collisions

Hash tables are one of the most versatile and widely used data structures in programming, and understanding them deeply will serve you well in JavaScript and beyond.

# Hash Map Collisions

A collision in a hash map (or hash table) occurs when two different keys produce the same hash value (index) when processed by the hash function. Since hash maps use an array of limited size to store data, collisions are inevitable and must be handled properly.

## How Collisions Happen

1. **Hash Function Limitations**: Even with a good hash function, multiple keys can map to the same index
   - Example: With table size 10, keys "apple" and "orange" might both hash to index 3

2. **Pigeonhole Principle**: If you have more items to store than available slots, collisions must occur
   - With 100 slots and 101 items, at least two items must share a slot

## Why Collisions Matter

Collisions degrade the performance of hash maps from their ideal O(1) time complexity toward O(n) in worst-case scenarios if not handled properly.

## Common Collision Resolution Techniques

### 1. Separate Chaining (Open Hashing) (refer the VS code for this code)

- **How it works**: Each array index (bucket) stores a linked list or array of key-value pairs
- **Implementation**:
  ```javascript
  [
    0: [ ['key1', 'value1'], ['key2', 'value2'] ], // Collision at index 0
    1: [ ['key3', 'value3'] ],
    2: null,
    // ...
  ]
  ```
- **Pros**:
  - Simple to implement
  - Hash table never fills up (can always add more items)
- **Cons**:
  - Requires extra memory for pointers/links
  - Cache performance isn't optimal

### 2. Open Addressing (Closed Hashing)

- **How it works**: When collision occurs, find next available slot using a probing sequence
- **Common probing methods**:
  - **Linear probing**: Check next slot (index+1, index+2, etc.)
  - **Quadratic probing**: Check index+1², index+2², index+3², etc.
  - **Double hashing**: Use a second hash function to determine step size

- **Implementation example** (linear probing):
  ```javascript
  class HashTable {
    constructor(size) {
      this.size = size;
      this.keys = new Array(size);
      this.values = new Array(size);
    }

    set(key, value) {
      let index = this._hash(key);
      
      while (this.keys[index] !== undefined && this.keys[index] !== key) {
        index = (index + 1) % this.size; // Linear probing
      }
      
      this.keys[index] = key;
      this.values[index] = value;
    }

    get(key) {
      let index = this._hash(key);
      let startIndex = index;
      
      while (this.keys[index] !== undefined) {
        if (this.keys[index] === key) {
          return this.values[index];
        }
        index = (index + 1) % this.size;
        
        // If we've looped all the way around
        if (index === startIndex) break;
      }
      
      return undefined;
    }
  }
  ```

- **Pros**:
  - Better cache performance (all data stored in one array)
  - No extra memory for pointers
- **Cons**:
  - More complex implementation
  - Table can fill up (requires resizing)
  - Clustering can occur (contiguous blocks of used slots)

## Real-World Impact of Collisions

1. **Performance Degradation**: Excessive collisions turn O(1) operations into O(n)
2. **Security Risks**: Attackers can exploit predictable hash functions to cause deliberate collisions (DoS attacks)
   - Modern languages use randomized hash functions to prevent this

## JavaScript-Specific Considerations

1. **Object Properties**: JavaScript objects use a hash table internally
   - Modern engines optimize property access but collisions still occur
   
2. **Map vs Object**: ES6 Maps handle collisions differently than plain objects
   - Maps typically use more sophisticated collision resolution

3. **Automatic Resizing**: JavaScript engines automatically resize the underlying storage when load factor becomes too high

## Best Practices to Minimize Collisions

1. **Good Hash Function**:
   - Distributes keys uniformly
   - Uses all bits of the key (not just some)
   - Is fast to compute

2. **Appropriate Table Size**:
   - Use prime numbers for table size (reduces clustering)
   - Maintain reasonable load factor (typically resize when > 0.7)

3. **Resizing Strategy**:
   - Double the size when threshold is reached **( rehashing--> [[#What is **Rehashing** in HashTable?]])
   - Rehash all existing items into new larger table

## Example of Collision in JavaScript

```javascript
// Simple hash function that creates collisions intentionally
function badHash(key, size) {
  return key.length % size; // Only depends on string length
}

const table = new Array(5);
table[badHash("apple", 5)] = "fruit";  // index: 5 % 5 = 0
table[badHash("orange", 5)] = "fruit"; // index: 6 % 5 = 1
table[badHash("kiwi", 5)] = "fruit";   // index: 4 % 5 = 4
table[badHash("banana", 5)] = "fruit"; // index: 6 % 5 = 1 - COLLISION with "orange"
```

In this example, "orange" and "banana" collide because they have the same length (6 characters) and thus produce the same hash value.

Understanding collisions is crucial for implementing efficient hash maps and diagnosing performance issues in hash-based data structures.



# What is **Rehashing** in HashTable?

**Rehashing** means:

- **Creating a new, larger hash table** when the current table is **too full**.
    
- **Re-inserting all existing key-value pairs into the new table using the hash function.**
    

It helps:  
✅ Reduce collisions.  
✅ Maintain fast O(1) access.  
✅ Avoid performance drops when many elements are added.

---

## 🚩 When is Rehashing Triggered?

✅ When the **load factor** exceeds a threshold.

**Load Factor = (number of elements) / (table size)**

Example:

- Table size = 10
    
- 7 elements inserted
    
- Load factor = 0.7
    

If the threshold is 0.7 or 0.75, rehashing is triggered.

---

## 🚩 How Rehashing is Done?

1️⃣ **Double the size of the hash table** (or increase to the next prime for fewer collisions).

2️⃣ Create a **new empty hash table of the new size**.

3️⃣ **For each key-value pair in the old table:**

- Calculate the **new index using the hash function on the new table size**.
    
- Insert into the new table using the collision resolution method (chaining/linear probing).
    

4️⃣ Replace the old table with the new table.

---

## 🚩 Example:

### Initial table:

Size = 5  
Hash function: `key % 5`

Keys inserted: 1, 6, 11

They all hash to `1 % 5 = 1`, `6 % 5 = 1`, `11 % 5 = 1` → collisions occur.

### Load factor after 3 insertions: `3/5 = 0.6`

If threshold = 0.6 → **rehashing is triggered**.

---

### Steps:

✅ New size = 10 (double)  
✅ New hash function: `key % 10`

Now:

- 1 → `1 % 10 = 1`
    
- 6 → `6 % 10 = 6`
    
- 11 → `11 % 10 = 1`
    

The keys are now distributed better:

```
Index 1 → 1, 11
Index 6 → 6
```

Reducing collisions, improving performance.

---

## 🚩 JavaScript Implementation (Linear Probing)

```javascript
class HashTable {
    constructor(size = 5) {
        this.table = new Array(size);
        this.size = size;
        this.count = 0;
    }

    hash(key) {
        if (typeof key === 'number') {
            return key % this.size;
        } else {
            let total = 0;
            for (let char of key) {
                total += char.charCodeAt(0);
            }
            return total % this.size;
        }
    }

    set(key, value) {
        if ((this.count + 1) / this.size > 0.7) {
            this.rehash();
        }

        let index = this.hash(key);
        while (this.table[index] !== undefined && this.table[index][0] !== key) {
            index = (index + 1) % this.size;
        }
        if (this.table[index] === undefined) {
            this.count++;
        }
        this.table[index] = [key, value];
    }

    get(key) {
        let index = this.hash(key);
        const startIndex = index;
        while (this.table[index] !== undefined) {
            if (this.table[index][0] === key) {
                return this.table[index][1];
            }
            index = (index + 1) % this.size;
            if (index === startIndex) break;
        }
        return undefined;
    }

    rehash() {
        console.log("Rehashing triggered...");
        const oldTable = this.table;
        this.size *= 2;
        this.table = new Array(this.size);
        this.count = 0;

        for (let pair of oldTable) {
            if (pair !== undefined) {
                this.set(pair[0], pair[1]);
            }
        }
    }

    display() {
        console.log(this.table);
    }
}

// Usage:
let ht = new HashTable(5);
ht.set(1, 'one');
ht.set(6, 'six');
ht.set(11, 'eleven');
ht.set(16, 'sixteen'); // triggers rehashing

ht.display();
```

---

## 🚩 Summary:

✅ **Rehashing = Resize + Reinsert** to avoid high load factor.  
✅ Triggered when **load factor crosses threshold** (commonly 0.7).  
✅ **Ensures consistent O(1) performance** in hash tables.  
✅ Helps **reduce collisions in growing data.**

---

If you want, I can also prepare:  
✅ A **visual diagram of rehashing with slots**.  
✅ **Interview cheat points** on rehashing.  
✅ A **chaining-based rehashing implementation** for comparison.

Let me know if you need these for your DSA revision.