# Lecture 5
### Contents
- CW Overview
- Lecture 4 finished
- Greedy Algorithms

---
### CW Overview
- It's out
- PAPER Submition

---
### Depth-first Search
```python
DFS(G,s):
let S ba a stack containing just the node s
let explored(v) = false for all v E V
while S is not empty
  pop v from the top of S
  if not explored(v) then
    for each edge{v,w} in E where not explored(w)
      push w onto S
      let parent(w) = v
    let explored(v) = true
```
**Running time:** O(n^2)

---
### Topological sorting
- Developed by NASA to organise work of thousands of people
- Shouldn't contain any cycles - acyclic

```python
TopologicalSort(G):
  let S be an empty stack
  for each vertex v E V
    compute indegree(v)
    if indegree(v) == 0 then push v onto S
  while S is not empty
    pop u from S
    schedule u
    for each (e,w) E E
      decrement indegree(w) by 1
      if indegree(w) = 0 then
        push w onto S
```

---
## Greedy Algorithms

### Interval Scheduling Problem
**Problem spec:**
- Two intervals are **compatible** if they have non-overlapping intervals
- **Input:** A set of intervals where each interval has a start and end time
- **Output:** The largest selection of compatible intervals that can be made
\
- Can be solved using so-called greedy approach

---
### Weighted Interval Scheduling
- Variant of Interval Scheduling Problem
- Each interval is assigned a **weight**

**Problem spec:**
- **Input:** set of intervals with start and finish times plus weights
- **Output:** subset of compatible intervals with the greatest total weight
\
- **Cannot be solved using the greedy approach**
- Use **dynamic programming** instead
  - Based on **divide-and-conquer**
  - Solutions to subproblems recorded in table

---
### Bipartite Matching
- **Input:** a graph that is bipartite
- **Output:** matching with most edges possible
\
- **Can be solved using the so-called network flow approach**

---
### Independent set
- **Input:** a graph
- **Output:** the largest independent set: no two nodes joined by edge
\
- NP-complete problem
  - no efficient algorithm known that solves this problem

---
### The Greedy Approach
- The algorithm makes a series of choices
- A solution is built up as these choices are made
- The **locally** bes option is made at each stage

**Works when:**
- no need to worry about what will happend in the future
- safe to commit to each decision
- no backtracking on decisions
- guarantee that the **globally** best solution will be found

**Interval Scheduling Algorithm**
```python
IntervalSchedule(I):

let Q be queue of intervals prioritised by the earliest end time
initialise A, the set of scheduled intervals, to be empty set
initialise current time k to be 0
while Q is not yet empty
  remove interval a from the front of Q
  if k <= s(a) then
    add the interval a to the set A
    set the current time k to be f(a)
return A
```

**RUNNING TIMES:**
- heap-based: Best-case O(n), worst-case  O(n log(n))
- unsorted list: Best-case O(n), worst-case O(n^2)

---
### The Shortest Path Problem
- **Problem Description:** Given a weighted graph G = (V,E) an edge weight function w and some s ∈ V the goal is to find the length of the shortest path to each vertex in V

**Dijkstra's Algorithm**
```python
Dijkstra(G,w,s):

let A be the empty set
let 𝛅(s) = 0
let 𝛅(v) = ∞ for v ∈ V - {s}
let Q be a priority queue containing elements of V
while Q is not empty
  remove v from front of pq Q
  add v to A
  for each {v,u} ∈ E where u ∉ A
    if 𝛅(u) > 𝛅(v) + w(v,u) then
      let 𝛅(u) = 𝛅(v) + w(v,u)

```

**Proving correctness of Dijkstra's Algorithm**
- **Claim:** as each v is added to A, 𝛅(v) is correct distance of v from s
- **Proof** by contradiction:
  - Suppose that v is first vertex added to A with wrong 𝛅(v)
  - Let p be a shortest path from s to v
  - So we know that w(p) < 𝛅(v)

- **Another Claim:** p must include a vertex not yet in A
- **Proof** by contradiction:
  - Suppose that p only includes vertices in A
  - Let u be the vertex immeditely vefore v on the path p
  - 𝛅(u) must be correct since v was first vertex with wrong value
  - We would have had 𝛅(v) = 𝛅(u) + w(u,v)
  - So 𝛅(v) would then had correct value w(p)
  - Yet later (when v added to A) w(p) < 𝛅(v)
  - Impossible: value of 𝛅(v) can't go up!
  - CARRY ON

**Running time of Dijkstra's Algorithm:**
- Q init -> O(n)
- Measure of progress -> number of vertices in A
- Loop executions -> n
- Updates of 𝛅 values with each iteration -> max. outdegree(v)
- Total of 𝛅 updates over all iter -> m
- Each update of a 𝛅 value -> O(log n)
- Total running time -> O(m log n)
- Can be written as -> O(n^2 log n)