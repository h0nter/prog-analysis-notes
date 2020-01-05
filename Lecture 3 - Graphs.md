# Lecture 3 - Graphs
### Adjecency matrix implementation
- Table of vertices against vertices, showing connections (edges) between them
- Good for dealing with: directed, undirected, cyclic, acyclic, weighted, unweighted
- Issues: space efficiency O(n^2), running time of basic operations

**Time efficiency:**
- O(1) - determine if there's an edge between 2 vertices
- O(n) - find all nodes adjacent to some node (even )
- Needs to enumerate adjacent nodes

---
### Adjecency list implementation
- List of vertices, each with its own list of adjacent vertices
- **Space efficiency**: O(m)

**Time efficiency:**
- O(1) - enumeration, per adjacent node
- O(n) - establish if the edge is in the graph
- Linear search of adjacency list
- List length O(n)

---
### Vertices and Edges
- **No edges:** m = 0
- **G is connected**: *m >= n - 1*
- **G is complete**: *m = n(n-1)/2* -> O(n^2)
- In general **m -> O(n^2)**

---
