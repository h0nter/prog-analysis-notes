# Lecture 6 - Greedy Algorithms 2
### The Minimum Spanning Tree (MST) Problem
**Soultion:**
- Consider edges in order of increasing weight and include in E' as long as no cycles
- Grow tree from aribitrary starting point
- Connect vertices closest to what has been built so far
- Consider edges in decreasing order of weight, exclude from G unless disconnecting the graph

**Cut Property:**
- Given graph G = (V,E)
- Split V into 2 disjoint sets
- The least weighted edge{u,v} - u E V1 and v E V2 - contained in every MST of G

**Cut Property Proof:**
...

### Kruskal's MST Algorithm
```python
Kruskal(G,w):

let Q be the edges in E ordered by increasing weight
init E` to be the empty set
for each vertex v ∈ V
  let C(v) be the singleton set containing v
while |E`| < |V| - 1
  remove edge {u,v} from Q
  if C(u) ≠ C(v) then
    include {u,v} in E`
    C(u) <- C(v) <- C(u) ∪ C(v)
return E`
```

**Running time:**
- **Measure of progress** - number of edges left in Q
- **Upper bound** - O(m)
- 