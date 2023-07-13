# Graph representation and traversal
## 1. **Question:**
Implement an undirected graph using an adjacency list and write a function to perform a depth-first traversal (DFS) starting from a given vertex.
### Solution:
 ```python
 class Graph:
   def __init__(self, num_vertices):
     self.num_vertices = num_vertices
     self.adj_list = [[] for _ in range(num_vertices)]
   def add_edge(self, u, v):
     self.adj_list[u].append(v)
     self.adj_list[v].append(u)
   def dfs(self, start_vertex):
     visited = [False] * self.num_vertices
     self._dfs_helper(start_vertex, visited)
   def _dfs_helper(self, vertex, visited):
     visited[vertex] = True
     print(vertex, end=" ")
     for neighbor in self.adj_list[vertex]:
       if not visited[neighbor]:
         self._dfs_helper(neighbor, visited)
 ```
## 2. **Question:**
Implement a directed graph using an adjacency matrix and write a function to perform a breadth-first traversal (BFS) starting from a given vertex.
### Solution:
 ```python
 class Graph:
   def __init__(self, num_vertices):
     self.num_vertices = num_vertices
     self.adj_matrix = [[0] * num_vertices for _ in range(num_vertices)]
   def add_edge(self, u, v):
     self.adj_matrix[u][v] = 1
   def bfs(self, start_vertex):
     visited = [False] * self.num_vertices
     queue = []
     queue.append(start_vertex)
     visited[start_vertex] = True
     while queue:
       vertex = queue.pop(0)
       print(vertex, end=" ")
       for neighbor in range(self.num_vertices):
         if self.adj_matrix[vertex][neighbor] == 1 and not visited[neighbor]:
           queue.append(neighbor)
           visited[neighbor] = True
 ```
## 3. **Question:**
Given a directed graph, write a function to check if it contains a cycle using depth-first search (DFS).
### Solution:
 ```python
 class Graph:
   def __init__(self, num_vertices):
     self.num_vertices = num_vertices
     self.adj_list = [[] for _ in range(num_vertices)]
   def add_edge(self, u, v):
     self.adj_list[u].append(v)
   def has_cycle(self):
     visited = [False] * self.num_vertices
     rec_stack = [False] * self.num_vertices
     for vertex in range(self.num_vertices):
       if not visited[vertex]:
         if self._has_cycle_helper(vertex, visited, rec_stack):
           return True
     return False
   def _has_cycle_helper(self, vertex, visited, rec_stack):
     visited[vertex] = True
     rec_stack[vertex] = True
     for neighbor in self.adj_list[vertex]:
       if not visited[neighbor]:
         if self._has_cycle_helper(neighbor, visited, rec_stack):
           return True
       elif rec_stack[neighbor]:
         return True
   rec_stack[vertex] = False
   return False
 ```
## 4. **Question:**
Given an undirected graph, write a function to find the shortest path between two vertices using breadth-first search (BFS).
### Solution:
 ```python
 class Graph:
   def __init__(self, num_vertices):
     self.num_vertices = num_vertices
     self.adj_list = [[] for _ in range(num_vertices)]
   def add_edge(self, u, v):
     self.adj_list[u].append(v)
     self.adj_list[v].append(u)
   def shortest_path(self, start_vertex, end_vertex):
     visited = [False] * self.num_vertices
     distance = [float('inf')] * self.num_vertices
     parent = [-1] * self.num_vertices
     queue = []
     queue.append(start_vertex)
     visited[start_vertex] = True
     distance[start_vertex] = 0
     while queue:
       vertex = queue.pop(0)
       for neighbor in self.adj_list[vertex]:
         if not visited[neighbor]:
           queue.append(neighbor)
           visited[neighbor] = True
           distance[neighbor] = distance[vertex] + 1
           parent[neighbor] = vertex
           if neighbor == end_vertex:
             return self._construct_path(parent, start_vertex, end_vertex)
     return []
   def _construct_path(self, parent, start_vertex, end_vertex):
     path = []
     current = end_vertex
     while current !=-1:
       path.append(current)
       current = parent[current]
     return path[::-1]
```
## 5. **Question:**
Given a weighted directed graph, write a function to find the shortest path between two vertices using Dijkstra's algorithm.
### Solution:
 ```python
 import heapq
 class Graph:
   def __init__(self, num_vertices):
     self.num_vertices = num_vertices
     self.adj_list = [[] for _ in range(num_vertices)]
   def add_edge(self, u, v, weight):
     self.adj_list[u].append((v, weight))
   def dijkstra(self, start_vertex):
     distance = [float('inf')] * self.num_vertices
     distance[start_vertex] = 0
     min_heap = []
     heapq.heappush(min_heap, (0, start_vertex))
     while min_heap:
       dist, vertex = heapq.heappop(min_heap)
       if dist > distance[vertex]:
         continue
       for neighbor, weight in self.adj_list[vertex]:
         new_dist = distance[vertex] + weight
         if new_dist < distance[neighbor]:
             distance[neighbor] = new_dist
             heapq.heappush(min_heap, (new_dist, neighbor))
   return distance
```
