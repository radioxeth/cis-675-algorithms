# Week 3: Graphs Part 1

- [Home](/README.md#async-table-of-contents)
- [3.1 Weekly Introductoin](#21-weekly-introduction)
- [3.2 Graphs](#32-graphs)
- [3.3 Depth-First Search (DFS)](#33-depth-first-search-dfs))
- [Week 3 Live Session](#week-3-live-session)

# 3.1 Weekly Introduction
([top](#week-3-graphs-part-1))

- Introduction to graphs, including discussion of how to represent graphs on a computer
- Basic graph terminology
- Depth-first search, an algorithm for exploring graphs
- Directed acyclic graphs

# 3.2 Graphs
([top](#week-3-graphs-part-1))

## Graphs
- Graph data structure
  1. **Nodes/vertices**
     - Let $V={v_1,v_2,...}$
  2. **Edges/links**
     - let $E={e_1,e_2,...}$
     - an edge is usually written as $(v_1,v_2)$ where $v_1$ and $v_2$ are vertices
- can be weighted: different edges have different strengths
- can be directed: edges point in one direction

## Graph Representation
- Adjacency Matrix:
  - suppose there are $n=|V|$
  - create an $nxn$ matrix $A$

### Exercise 3.2.2
*Daniel Shannon*
> How much space does the adjacency matrix take?

The adjacency matrix takes $n^2$ space, where $n$ is the number of nodes.

## Terminology
- two *nodes* are **adjacent** if they are connected by an edge.
- two *edges* are **adjacent** if thy have one vertex in common.
- a **path** is a sequence of adjacent edges froma vertex *v* to another vertex *u*.
- a **component** is a set of vertices such that there exists a path between every pair of vertices in the set.

## 3.3 Depth-First Search (DFS)
([top](#week-3-graphs-part-1))

>```
>procedure explore(G,v)
>Input:  G(V,E) is a graph; v is in V
>Output: visited(u) is set to true for all nodes u reachable from v
>previsit(v)
>visisted(v)=true
>for each edge (v,u) in E:
>  if not visited(u): explore(u)
>postvisit(v)
>```
>
>```
>procedure previsit(v)
>pre[v]=clock
>clock=clock+1
>```
>```
>procedure postvisit(v)
>post[v]=clock
>clock=clock+1
>```
> 
