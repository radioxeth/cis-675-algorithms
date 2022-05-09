# Week 5: Greedy Algorithms, Linear Programming

- [Home](/README.md#async-table-of-contents)
- [5.1 Weekly Introductoin](#51-weekly-introduction)
- [5.2 Greedy Algorithms](#52-greedy-algorithms)
- [Week 5 Live Session](#week-5-live-session)

## Questions
- Why use BFS over DFS or visa versa?
  - BFS is shortest path
  - DFS is exploring paths
- Any analaysis to be done comparing the DFS tree to the BFS tree?

## 5.1 Weekly Introduction
([top](#week-5-greedy-algorithms-linear-programming))

- Introduction to greedy algorithms
- Examples of greedy algorithms
- Linear programming
- Network flows

## 5.2 Greedy Algorithms
([top](#week-5-greedy-algorithms-linear-programming))

- For some algorithms, you need to look ahead or revise past decisison to get the best solution
- **Greedy algorithms** build a solution piece by piece, without revising past decisions

### Spanning Trees
- we want to find spanning trees in an undirected graph
  - a spanning tree is a tree that touches every node
  - how do we find spanning trees?

1. A graph is a tree
2. A graph has n-1 edges and n nodes, it is connected
3. a graph is connected an acyclic


Rules
1. Don't add an edge if it would create a cycle
2. A tree on n nodes must have n-1 edges
3. an undirected graph is a tree if and only iff there is one unique path between every pair of nodes

- **minimum spanning tree** is an undirected weighted graph is the spanning tree with minimum total weight

### Kruskal's algorithm
1. sort the edges from least cost to greatest cost
2. Add each edge in order to the spanning tree unless it would make a cycle

- at each step, we have a set of connected components
- initially, every vertex is its own component
- add edges in order of weight, but don't add edges that lie within one component
    - why not? this would create a cycle

- Could run DFS/BFS everytime we add an edge to the component to make sure it doesn't create an edge.
### Kruskal's Idea
- Idea:  associate each node with a "representative" node from the same component
- Union-find data structure supports three operations
  - `Makeset(v)`: makes a set containing just v
  - `Find(v)`: which set/component does v belong to?
    - eg who is v's representative?
  - `Union(u,v)`: Merge the sets containing u and v

- sort edges
- add each edge without creating a cycle

### Prim's Algorithm
- start with a random node
- at each step, add the lightest edge leading out of the current node set
- what does this remind you of? (dijkstra)

### Fractional Knapsack
- you are given a collection of items
- each item *i* has weight $w_i$ and a value $v_i$
- you have bag that can hold a total weight of W.
- you want to maximize the value of the items in your bag (assume you can take fractional items)
- Design an algorithm to decide which items to pick

### Set Cover
- Given a set of elements B, and sets S1...Sk that are subsets of B
- How many sets Si, do you need to pick so that every element from B appears in at least one selected set?

## Week 5 Live Session