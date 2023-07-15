# Breadth-First Search (BFS) algorithm
## 1. **Question:**
Implement the Breadth-First Search (BFS) algorithm in Python.
### Solution:
 ```python
 from collections import deque
   def bfs(graph, start):
     visited = set()
     queue = deque([start])
     while queue:
       node = queue.popleft()
       if node not in visited:
         visited.add(node)
         print(node, end=' ')
         for neighbor in graph[node]:
           if neighbor not in visited:
             queue.append(neighbor)
 ```
## 2. **Question:**
Given the following graph, apply the BFS algorithm starting from vertex 'A':
```
graph = {
 'A': ['B', 'C'],
 'B': ['D', 'E'],
 'C': ['F'],
 'D': [],
 'E': ['F'],
 'F': []
 }
 ```
# Solution:
The BFS traversal starting from vertex 'A' would be: A, B, C, D, E, F.
## 3. **Question:**
Explain the purpose of using a visited set in the BFS algorithm.
### Solution:
The visited set is used in the BFS algorithm to keep track of the nodes that have been visited to avoid processing them multiple times. It ensures that each node is visited exactly once and prevents cycles in the graph from causing an infinite loop.
## 4. **Question:**
What is the time complexity of the BFS algorithm on a graph with V vertices and E edges?
### Solution:
The time complexity of BFS is O(V + E), where V is the number of vertices and E is the number of edges in the graph. It visits each vertex and edge once, resulting in a linear runtime complexity.
## 5. **Question:**
How would you modify the BFS algorithm to find the shortest path between two vertices in an unweighted graph?
### Solution:
To find the shortest path between two vertices using BFS, you can keep track of the parent of each node while traversing the graph. Once the destination vertex is reached, you can backtrack from the destination to the source using the parent information to reconstruct the shortest path.
