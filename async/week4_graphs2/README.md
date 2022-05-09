# Week 4: Graphs Part 2

- [Home](/README.md#async-table-of-contents)
- [4.1 Weekly Introductoin](#41-weekly-introduction)
- [4.2 Breadth-First Search (BFS)](#42-breadth-first-search-bfs)
- [4.3 Dijkstra's Algorithm](#43-dijkstras-algorithm)
- [4.4 Bellman-Ford Algorithm](#44-bellman-ford-algorithm)
- [4.5 Shortest Paths on DAGs](#45-shortest-paths-on-dags)
- [4.6 Heaps](#46-heaps)
- [Week 4 Live Session](#week-4-live-session)

## Questions
- Why use BFS over DFS or visa versa?
  - BFS is shortest path
  - DFS is exploring paths
- Any analaysis to be done comparing the DFS tree to the BFS tree?

## 4.1 Weekly Introduction
([top](#week-4-graphs-part-2))

- Breadth-first search, an algorithm for exploring graphs
- Dijkstra's algorithm for finding shortest paths
- Bellman-Ford algorithm for finding shortest paths
- Finding shortest paths on DAGs
- Min-heap data structure

## 4.2 Breadth-First Search (BFS)
([top](#week-4-graphs-part-2))

```
procedure bgf(G,s)
Input:  Graph G = (V,E), directed or undirected; vertex s in V
Output: For all vertices u reachable from s, dist(u) is set to the distance from s to u.

for all u in V:
  dist(u)=infin

dist(s)=0
Q=[s] (queue containing just s)
while Q is not empty:
  u = eject(Q)
  for all edges (u,v) in E: //put all neighbors on queue
    if dist(v) == infin:
      inject(Q,v)
      dist(v)=dist(u)+1 //distance to neighbor=1 + distance to current node
```

stack - LIFO
queue - FIFO

### Shortest Path via BFS

Running time is $O(n)$ to initialize. $O(E(u,v))$ to execute DFS. O(E) out weighs O(N), so O(E) is our running time.

## 4.3 Dijkstra's Algorithm
([top](#week-4-graphs-part-2))

```
for all u in V:
  dist(u)=infin
  prev(u)=null
dist(s)=0

H=makequeue(V) (use dist-values as keys)
while H is not empty
  u-deletemin(H)
  for all edges (u,v) in E:
    if dist(v)>dist(u)+length(u,v):
      dist(v)=dist(u)+length(u,v)
      prev(v)=u
      decreasekey(H,v)
```

## 4.4 Bellman-Ford Algorithm
([top](#week-4-graphs-part-2))

## 4.5 Shortest Paths on DAGs
([top](#week-4-graphs-part-2))


## 4.6 Heaps
([top](#heaps))

- Dijkstra's algorithm uses a priority queue:
  - Insert
  - Decrease-key
  - Delete-min
- Suppose we implement them as an array, where A[i] holds key of node i
- What is the running time for delete-min
- For decrease-key? 

### Binary Heaps
- A **binary heap** is a complete binary tree
  - every level must be full before a new level is started
- key-value of any node is less than or equal to those of its children
- Which elelment has the smallest value?
  - *the root element*

- How do we delete-min?
  - Return the root values
  - Delete the root
  - take the last element in the tree (lowest level, furthest right) and put it in the root element.
  - Swap that element with whichever of its children are smallest and let it sift down

- delete-min
  $O(log(n)$ run time

- How do we insert?
  - Place the new element in the first empty spot (bottom level, furthest right)
  - Let it "bubble up" by swapping it with its parent, for as long as the parent is larger

### Later in the course
- DAGs
- Dynamic programming
- Linearizations
- Shortest paths on DAGs

## Week 4 Live Session

Running time of BFS is O(|E|) or (O(n-1))

In an unweighted

Shortest path principle Belmman Ford
- Shortest path is an invariant
- negative edge graphs break the *assumption* that there is a single shortest path
- if you can't find a shortest path, your problem is ill-defined.