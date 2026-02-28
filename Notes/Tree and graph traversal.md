---
date: 2026-02-20
tags:
  - algorithms
  - data-structures
---
## Key concepts
- A tree is just a graph with no cycles
- A graph needs a visited set to track where you've been

## Breadth First Search
- An alg used to explore nodes in a graph/tree level by level
- Starts at a given node and explores all neighbours, then neighbours neighbours, etc
- BFS uses a **queue** to decide which node to explore
- Best for **shortest path**

GRAPH BFS: [[Python Graph BFS]]

## Depth First Search
- Goes as deep as possible in one path before going to the next node
- Uses **stack** (recursion)
- Best for **exploring all paths**

TREE DFS: [[Python Tree DFS]]

DFS RECURSIVE: [[Python Recursive DFS]]

DFS ITERATIVE: [[Python Iterative DFS]]

## Heaps
- **Min heap** - smallest value is the root and each parent is smaller than its children
- **Max heap** - largest is at the root
- Opposite to find k largest/smallest
