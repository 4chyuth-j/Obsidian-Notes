# 🚀Graph Data Structure in JavaScript

Graphs are one of the most versatile and powerful data structures in computer science. Let me explain them in a beginner-friendly way.

![[Pasted image 20250729012413.png]]
## What is a Graph?

A **graph data structure** is a way to represent **relationships** or **connections** between a set of elements. It's like a map or network, where:

- **Nodes (also called vertices)** represent entities (like people, cities, or computers).
    
- **Edges (or links)** represent connections between those entities (like friendships, roads, or network cables).
---
                                  or

---



A graph is a collection of nodes (also called vertices) connected by edges. Think of it like a social network:
- Each person is a node
- Each friendship is an edge connecting two nodes

Unlike trees, graphs can have cycles (loops) and nodes can connect to any other nodes.

## Graph Terminology

1. **Vertex (Node)**: The fundamental unit of the graph (like a person in a social network)
2. **Edge**: The connection between two vertices (like a friendship)
3. **Directed Graph**: Edges have direction (one-way relationships)
4. **Undirected Graph**: Edges have no direction (two-way relationships)
5. **Weighted Graph**: Edges have values/weights (like distance between cities)
6. **Cycle**: A path that starts and ends at the same vertex
7. **Degree**: Number of edges connected to a vertex
8. **Path**: Sequence of vertices connected by edges
9. **Connected Graph**: There's a path between every pair of vertices
10. **Disconnected Graph**: Some vertices have no path between them

## Types of Graphs

1. **Undirected Graph**: 
   - Edges have no direction
   - Example: Facebook friendships (if you're friends with someone, they're friends with you)

2. **Directed Graph (Digraph)**:
   - Edges have direction
   - Example: Twitter follows (you can follow someone without them following you back)

3. **Weighted Graph**:
   - Edges have values/weights
   - Example: Maps with distances between cities

4. **Unweighted Graph**:
   - Edges have no values
   - Example: Simple social network connections

5. **Cyclic Graph**:
   - Contains at least one cycle
   - Example: A->B->C->A

6. **Acyclic Graph**:
   - Contains no cycles
   - Example: Tree structure

## Implementing Graphs in JavaScript

There are two main ways to represent graphs in code:

### 1. Adjacency List (Most common in JS)
![[Pasted image 20250729013348.png]]
![[Pasted image 20250729013512.png]]

```javascript
// Undirected, unweighted graph
class Graph {
  constructor() {
    this.adjacencyList = {};
  }

  addVertex(vertex) {
    if (!this.adjacencyList[vertex]) {
      this.adjacencyList[vertex] = [];
    }
  }

  addEdge(v1, v2) {
    this.adjacencyList[v1].push(v2);
    this.adjacencyList[v2].push(v1); // For directed graph, remove this line
  }

  removeEdge(v1, v2) {
    this.adjacencyList[v1] = this.adjacencyList[v1].filter(v => v !== v2);
    this.adjacencyList[v2] = this.adjacencyList[v2].filter(v => v !== v1);
  }

  removeVertex(vertex) {
    while (this.adjacencyList[vertex].length) {
      const adjacentVertex = this.adjacencyList[vertex].pop();
      this.removeEdge(vertex, adjacentVertex);
    }
    delete this.adjacencyList[vertex];
  }
}

// Example usage
const graph = new Graph();
graph.addVertex("Tokyo");
graph.addVertex("London");
graph.addVertex("New York");
graph.addEdge("Tokyo", "London");
graph.addEdge("New York", "London");
```

### 2. Adjacency Matrix
```javascript
// For a graph with 3 vertices (0, 1, 2)
const matrix = [
  [0, 1, 0], // Vertex 0 is connected to vertex 1
  [1, 0, 1], // Vertex 1 is connected to vertices 0 and 2
  [0, 1, 0]  // Vertex 2 is connected to vertex 1
];
```
![[Pasted image 20250729013109.png]]
![[Pasted image 20250729013128.png]]

### Adjacency matrix vs adjacency list

![[Pasted image 20250729014304.png]]
## Graph Traversal Algorithms

### 1. Depth-First Search (DFS) - Uses a stack
```javascript
depthFirstRecursive(start) {
  const result = [];
  const visited = {};
  const adjacencyList = this.adjacencyList;

  (function dfs(vertex) {
    if (!vertex) return null;
    visited[vertex] = true;
    result.push(vertex);
    adjacencyList[vertex].forEach(neighbor => {
      if (!visited[neighbor]) {
        return dfs(neighbor);
      }
    });
  })(start);

  return result;
}
```

### 2. Breadth-First Search (BFS) - Uses a queue
```javascript
breadthFirst(start) {
  const queue = [start];
  const result = [];
  const visited = {};
  visited[start] = true;
  
  while (queue.length) {
    const currentVertex = queue.shift();
    result.push(currentVertex);
    
    this.adjacencyList[currentVertex].forEach(neighbor => {
      if (!visited[neighbor]) {
        visited[neighbor] = true;
        queue.push(neighbor);
      }
    });
  }
  return result;
}
```

## Applications of Graphs

1. **Social Networks**: Friends connections (Facebook, LinkedIn)
2. **Maps/Navigation**: Roads between locations (Google Maps)
3. **Web Pages**: Links between websites (Google's PageRank)
4. **Recommendation Systems**: "People who bought this also bought..."
5. **Computer Networks**: Network topology, packet routing
6. **Dependency Management**: npm packages, build systems
7. **Artificial Intelligence**: State space search
8. **Biology**: Protein interaction networks

## Advantages of Graphs

1. **Versatile**: Can model many real-world systems
2. **Efficient relationships**: Great for complex connections
3. **Path finding**: Algorithms like Dijkstra's can find shortest paths
4. **Flexibility**: Can represent hierarchical or non-hierarchical data

## Disadvantages of Graphs

1. **Complexity**: Harder to understand than linear data structures
2. **Memory usage**: Can consume more memory than simpler structures
3. **Algorithm complexity**: Some graph algorithms are computationally expensive
4. **Implementation**: More complex to implement than arrays or linked lists

## Time and Space Complexities

| Operation       | Adjacency List | Adjacency Matrix |
|-----------------|----------------|------------------|
| Add Vertex      | O(1)           | O(V²)            |
| Add Edge        | O(1)           | O(1)             |
| Remove Vertex   | O(V + E)       | O(V²)            |
| Remove Edge     | O(E)           | O(1)             |
| Query           | O(V + E)       | O(1)             |
| Storage         | O(V + E)       | O(V²)            |

Where V = number of vertices, E = number of edges

## Common Graph Algorithms

1. **Dijkstra's Algorithm**: Shortest path in a weighted graph
2. **Bellman-Ford Algorithm**: Shortest path with negative weights
3. **Prim's/Kruskal's Algorithms**: Minimum spanning trees
4. **Topological Sorting**: For directed acyclic graphs (DAGs)
5. **Floyd-Warshall Algorithm**: All pairs shortest paths
6. **A* Search**: Informed pathfinding algorithm

## When to Use Graphs

Use graphs when:
- You need to represent complex relationships
- Your data has many-to-many relationships
- You need to find paths or connections
- Your data is naturally networked

Don't use graphs when:
- Your data is simple and linear
- You don't need relationship information
- Memory is extremely limited

Graphs are powerful tools that can model many real-world systems. While they have a steeper learning curve than simpler data structures, mastering graphs will give you powerful ways to solve complex problems.

# 🚀**Types of Graphs in Data Structures**  

Graphs can be classified into different types based on their **direction, weight, connectivity, and structure**. Here’s a detailed breakdown of the most common types of graphs:

---

## **1. Based on Direction of Edges**  

### **(a) Undirected Graph**  
![[Pasted image 20250729012721.png]]
- **Edges have no direction** (bidirectional).  
- If there’s an edge between `A` and `B`, you can go from `A → B` and `B → A`.  
- Example: Facebook friendships (if you’re friends, both can see each other).             

**Representation:**  
```javascript
{
  'A': ['B', 'C'],
  'B': ['A'],
  'C': ['A']
}
```

### **(b) Directed Graph (Digraph)** 
![[Pasted image 20250729012655.png]]
- **Edges have direction** (one-way).  
- If `A → B`, you can go from `A` to `B` but not necessarily back.  
- Example: Twitter follows (you follow someone, but they may not follow you back).  

**Representation:**  
```javascript
{
  'A': ['B'],  // A follows B
  'B': ['C'],  // B follows C
  'C': []      // C follows no one
}
```

---

## **2. Based on Edge Weights**  

### **(a) Unweighted Graph**  
- **Edges have no weights** (all connections are equal).  
- Example: Metro stations (just connections, no distance considered).  

### **(b) Weighted Graph**  
- **Edges have weights** (e.g., distance, cost, time).  
- Example: Google Maps (roads have travel time/distance).  

**Representation (Adjacency List with Weights):**  
```javascript
{
  'A': [{ node: 'B', weight: 5 }, { node: 'C', weight: 2 }],
  'B': [{ node: 'A', weight: 5 }],
  'C': [{ node: 'A', weight: 2 }]
}
```

---

## **3. Based on Connectivity**  

### **(a) Connected Graph**  
- **All nodes are connected** (you can reach any node from any other node).  
- Example: A fully linked friend group.  

### **(b) Disconnected Graph**  
- **Some nodes are unreachable** (there are isolated subgraphs).  
- Example: Two separate friend circles with no common connection.  

**Example:**  
```javascript
{
  'A': ['B'],  // Group 1
  'B': ['A'],
  'C': ['D'],  // Group 2 (disconnected from Group 1)
  'D': ['C']
}
```

---

## **4. Based on Cycles**  

### **(a) Cyclic Graph**  
- **Contains at least one cycle** (a path that starts and ends at the same node).  
- Example: `A → B → C → A` (forms a loop).  

### **(b) Acyclic Graph**  
- **No cycles exist** (no loops).  
- Example: Family tree (no one can be their own ancestor).  

**Special Case:**  
- **Directed Acyclic Graph (DAG)**: A directed graph with no cycles.  
  - Used in **task scheduling, dependency resolution (npm packages)**.  

---

## **5. Special Types of Graphs**  

### **(a) Tree**  
- A **connected, undirected, acyclic** graph.  
- Example: File system hierarchy, DOM tree.  

### **(b) Complete Graph**  
- **Every node is connected to every other node**.  
- Example: A group where everyone knows everyone else.  

### **(c) Bipartite Graph**  
- **Nodes can be divided into two groups**, where edges only connect nodes from different groups.  
- Example: Job applicants (Group 1) and job openings (Group 2).  

### **(d) Sparse vs. Dense Graphs**  
- **Sparse**: Few edges compared to nodes (e.g., social network with few friends).  
- **Dense**: Many edges (e.g., a fully connected team chat group).  

---

## **Summary Table of Graph Types**  

| **Category**       | **Type**           | **Description**                          | **Example**                     |
|--------------------|--------------------|------------------------------------------|----------------------------------|
| **Direction**      | Undirected         | Edges have no direction (bidirectional)  | Facebook friendships             |
|                    | Directed (Digraph) | Edges have direction (one-way)           | Twitter follows                  |
| **Weights**        | Unweighted         | All edges are equal                      | Social connections               |
|                    | Weighted           | Edges have values (distance, cost)       | Google Maps                      |
| **Connectivity**   | Connected          | All nodes are reachable                  | Fully linked network             |
|                    | Disconnected       | Some nodes are isolated                  | Two separate friend groups       |
| **Cycles**         | Cyclic             | Contains at least one loop               | Circular dependencies            |
|                    | Acyclic            | No loops                                 | Family tree                      |
| **Special Types**  | Tree               | Connected, undirected, no cycles         | File system                      |
|                    | Complete Graph     | Every node connects to every other       | Fully connected team             |
|                    | Bipartite          | Nodes split into two groups              | Job applicants & job openings    |

---

## **Which Graph Type Should You Use?**  
- **Social networks?** → Undirected, unweighted.  
- **Google Maps?** → Weighted, directed (one-way streets).  
- **Dependency management?** → Directed Acyclic Graph (DAG).  
- **Job matching?** → Bipartite graph.  

Understanding these types helps in **choosing the right graph** for your problem! 🚀








# 🚀Connected Components in Graphs

Connected components are fundamental concepts in graph theory that help us understand how a graph is structured. Let me explain this in simple terms.

## What Are Connected Components?

A connected component is a **subgraph** (a smaller part of the main graph) where:
- Every pair of vertices is connected by a path
- No vertex in the component is connected to any vertex outside the component

Think of it like islands:
- Each island is a connected component
- All towns on an island are connected by roads (edges)
- There are no roads between different islands

## Types of Connected Components

### 1. For Undirected Graphs
In undirected graphs, a connected component is a **maximal set of vertices where there's a path between every pair of vertices**.

Example:
```
A -- B    C -- D
 \  /      \  /
   E        F

G -- H -- I
     |
     J
```
This graph has **3 connected components**:
1. {A, B, E}
2. {C, D, F}
3. {G, H, I, J}

### 2. For Directed Graphs (Strongly Connected Components)
In directed graphs, we talk about **strongly connected components (SCCs)** - where there's a directed path from every vertex to every other vertex in the component.

Example:
```
A → B → C ← D
↑   ↓   ↑   ↓
E ← F   G → H
```
This has 4 SCCs:
1. {A, B, E, F} (can all reach each other)
2. {C}
3. {D}
4. {G, H}

## How to Find Connected Components

Here's how we can find connected components using Depth-First Search (DFS) in JavaScript:

```javascript
class Graph {
  constructor() {
    this.adjacencyList = {};
  }

  addVertex(vertex) {
    if (!this.adjacencyList[vertex]) this.adjacencyList[vertex] = [];
  }

  addEdge(v1, v2) {
    this.adjacencyList[v1].push(v2);
    this.adjacencyList[v2].push(v1); // For undirected graph
  }

  findConnectedComponents() {
    const visited = {};
    const components = [];
    
    for (let vertex in this.adjacencyList) {
      if (!visited[vertex]) {
        const component = [];
        this.dfs(vertex, visited, component);
        components.push(component);
      }
    }
    
    return components;
  }

  dfs(vertex, visited, component) {
    visited[vertex] = true;
    component.push(vertex);
    
    for (const neighbor of this.adjacencyList[vertex]) {
      if (!visited[neighbor]) {
        this.dfs(neighbor, visited, component);
      }
    }
  }
}

// Example usage
const graph = new Graph();
graph.addVertex('A'); graph.addVertex('B'); graph.addVertex('C');
graph.addVertex('D'); graph.addVertex('E'); graph.addVertex('F');
graph.addEdge('A', 'B'); graph.addEdge('B', 'C'); graph.addEdge('D', 'E');

console.log(graph.findConnectedComponents());
// Output: [ ['A', 'B', 'C'], ['D', 'E'], ['F'] ]
```

## Real-World Applications

1. **Social Networks**: Finding friend groups or communities
2. **Network Analysis**: Identifying clusters in computer networks
3. **Image Processing**: Finding regions in pixel connectivity
4. **Epidemiology**: Tracking disease spread through contact networks
5. **Web Crawling**: Grouping related websites

## Key Properties

1. **A connected graph has exactly one component** (the whole graph itself)
2. **A disconnected graph has multiple components**
3. **Isolated vertices** (with no edges) are their own components
4. The **component count** is a measure of graph connectivity

## Time Complexity

Finding connected components using DFS/BFS takes **O(V + E)** time where:
- V = number of vertices
- E = number of edges

This is efficient because we visit each vertex and edge exactly once.

## Why Are Connected Components Important?

1. They help **analyze network structure**
2. They're used in **cluster analysis**
3. They help **optimize algorithms** by processing components separately
4. They reveal **hidden patterns** in data

Connected components give us a way to break down complex graphs into understandable, independent parts - much like identifying separate communities in a large social network.














# 🚀Practical Graph Implementation ( along with BFS & DFS)

Let's create a complete, practical implementation of a Graph data structure in JavaScript with methods to:
1. Add vertices
2. Add edges
3. Perform Depth-First Search (DFS)
4. Perform Breadth-First Search (BFS)
5. Shortest Path (Unweighted Graph)

## Complete Graph Implementation

```javascript
class Graph {
  constructor() {
    this.adjacencyList = {};
  }

  // 1. Add Vertex
  addVertex(vertex) {
    if (!this.adjacencyList[vertex]) {
      this.adjacencyList[vertex] = [];
      console.log(`Added vertex: ${vertex}`);
    } else {
      console.log(`Vertex ${vertex} already exists`);
    }
  }

  // 2. Add Edge (undirected)
  addEdge(vertex1, vertex2) {
    if (!this.adjacencyList[vertex1] || !this.adjacencyList[vertex2]) {
      console.log("One or both vertices don't exist");
      return;
    }
    
    this.adjacencyList[vertex1].push(vertex2);
    this.adjacencyList[vertex2].push(vertex1);
    console.log(`Added edge between ${vertex1} and ${vertex2}`);
  }

  // 3. Depth-First Search (DFS) - Recursive
  dfsRecursive(start) {
    const visited = {};
    const result = [];

    const dfs = (vertex) => {
      if (!vertex) return;

      visited[vertex] = true;
      result.push(vertex);

      for (let neighbor of this.adjacencyList[vertex]) {
        if (!visited[neighbor]) {
          dfs(neighbor);
        }
      }
  };

  dfs(start);
  return result;
}

  // 4. Breadth-First Search (BFS)
  bfs(start) {
    const queue = [start];
    const result = [];
    const visited = {};
    visited[start] = true;
    
    while (queue.length) {
      const currentVertex = queue.shift();
      result.push(currentVertex);
      
      this.adjacencyList[currentVertex].forEach(neighbor => {
        if (!visited[neighbor]) {
          visited[neighbor] = true;
          queue.push(neighbor);
        }
      });
    }
    
    return result;
  }

  //Shortest path in unweighted graph
   shortPath(start,end){
        let queue = [[start]];
        let visited = new Set();
        while(queue.length){
            let path = queue.shift();
            let node = path[path.length-1];
            
            if(node == end) return path;
            if(!visited.has(node)){
                visited.add(node);
                for(let item of this.adjList[node]){
                    queue.push([...path,item]);
                }
            }
        }
        
        return null;
    }

  // Helper method to visualize the graph
  printGraph() {
    console.log("Current Graph Structure:");
    for (let vertex in this.adjacencyList) {
      console.log(`${vertex} -> ${this.adjacencyList[vertex].join(', ')}`);
    }
  }
}
```

## Practical Example Usage

Let's create a graph and test all the functionality:

```javascript
// Create a new graph
const socialNetwork = new Graph();

// Add vertices (people)
socialNetwork.addVertex("Alice");
socialNetwork.addVertex("Bob");
socialNetwork.addVertex("Charlie");
socialNetwork.addVertex("Diana");
socialNetwork.addVertex("Eve");

// Add edges (friendships)
socialNetwork.addEdge("Alice", "Bob");
socialNetwork.addEdge("Alice", "Charlie");
socialNetwork.addEdge("Bob", "Diana");
socialNetwork.addEdge("Charlie", "Eve");
socialNetwork.addEdge("Diana", "Eve");

// Print the current graph structure
socialNetwork.printGraph();
/* Output:
Current Graph Structure:
Alice -> Bob, Charlie
Bob -> Alice, Diana
Charlie -> Alice, Eve
Diana -> Bob, Eve
Eve -> Charlie, Diana
*/

// Perform DFS starting from Alice
console.log("DFS starting from Alice:", socialNetwork.dfsRecursive("Alice"));
// Output: DFS starting from Alice: ["Alice", "Bob", "Diana", "Eve", "Charlie"]

// Perform BFS starting from Alice
console.log("BFS starting from Alice:", socialNetwork.bfs("Alice"));
// Output: BFS starting from Alice: ["Alice", "Bob", "Charlie", "Diana", "Eve"]

// Add an isolated vertex (no edges)
socialNetwork.addVertex("Frank");
socialNetwork.printGraph();
/* Output:
Current Graph Structure:
Alice -> Bob, Charlie
Bob -> Alice, Diana
Charlie -> Alice, Eve
Diana -> Bob, Eve
Eve -> Charlie, Diana
Frank -> 
*/

// DFS from Frank (isolated vertex)
console.log("DFS starting from Frank:", socialNetwork.dfsRecursive("Frank"));
// Output: DFS starting from Frank: ["Frank"]
```

## Key Differences Between DFS and BFS

| Feature          | DFS (Depth-First Search)       | BFS (Breadth-First Search)     |
|------------------|-------------------------------|-------------------------------|
| Approach         | Goes deep first               | Explores neighbors first      |
| Data Structure   | Uses stack (implicit in recursion) | Uses queue                |
| Order            | Visits children before siblings | Visits siblings before children |
| Memory          | Generally uses less memory    | Uses more memory              |
| Best for        | Finding if path exists, topological sort | Shortest path, closest nodes |

This implementation gives you a complete, practical graph that you can use in real applications. You can easily extend it to handle directed graphs or weighted edges by modifying the `addEdge` method.