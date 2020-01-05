# Lecture 4 - Graphs Traversal and Topological Sort
### Traversing Graphs
- **Goal:** visit each node in a graph in a **systematic way**
- Non-linear
- Non-hierarchical

**Graph component:**
- a subset of the vertices in G and all associated edges from G
- must be connected
  - path between any pair of vertices
- must be maximal
  - cannot be enlarged and remain connected

**Solutions:**
- Breadth-first Search 
```
BFS(G,s):

let Q be a queue containing just the node 's'
let discovered(s) = true
let discovered(v) = false for all v ∊ V - {s}
let T = (V,{})
while Q is not empty
  remove v from the front of Q
  for each edge {v,w} in E where not discovered(w)
    let discovered(w) = true
    add w to the back of Q
    add edge {v,w} to edges in T

```
- Breadth-first Search for Multicomponent Graphs
```
BFS(G):

let discovered(v) = false for all v ∊ V
let T = (V, {})
for each v ∊ V
  if not discovered(v)
    BFS(G,v)
```

- **BFS time performance**: O(n+m)
  - the more the graph connected, bigger the m => m -> ^2

