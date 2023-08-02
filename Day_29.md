# Network flow: Ford fulkerson, Edmonds-karp :
## 1. **Question:**
Implement the Ford-Fulkerson algorithm to find the maximum flow in a flow network from a source vertex to a sink vertex.
### Solution:
 ```python
 class Graph:
   def __init__(self, num_vertices):
     self.num_vertices = num_vertices
     self.adjacency_matrix = [[0] * num_vertices for _ in range(num_vertices)]
   def add_edge(self, src, dest, capacity):
     self.adjacency_matrix[src][dest] = capacity
   def ford_fulkerson(self, source, sink):
     parent = [-1] * self.num_vertices
     max_flow = 0
   while self.bfs(source, sink, parent):
     path_flow = float('inf')
     s =sink
     while s != source:
       path_flow = min(path_flow, self.adjacency_matrix[parent[s]][s])
       s =parent[s]
       max_flow += path_flow
       v =sink
       while v != source:
         u =parent[v]
         self.adjacency_matrix[u][v]-= path_flow
         self.adjacency_matrix[v][u] += path_flow
         v =parent[v]
   return max_flow
   def bfs(self, source, sink, parent):
     visited = [False] * self.num_vertices
     queue = []
     queue.append(source)
     visited[source] = True
     while queue:
       u =queue.pop(0)
       for v in range(self.num_vertices):
         if not visited[v] and self.adjacency_matrix[u][v] > 0:
             queue.append(v)
             visited[v] = True
             parent[v] = u
     return visited[sink]
 ```
# 2. **Question:**
Implement the Edmonds-Karp algorithm to find the maximum flow in a flow network from a source vertex to a sink vertex.
### Solution:
 ```python
 class Graph:
   def __init__(self, num_vertices):
     self.num_vertices = num_vertices
     self.adjacency_matrix = [[0] * num_vertices for _ in range(num_vertices)]
   def add_edge(self, src, dest, capacity):
     self.adjacency_matrix[src][dest] = capacity  
   def edmonds_karp(self, source, sink):
     parent = [-1] * self.num_vertices
     max_flow = 0
     while self.bfs(source, sink, parent):
       path_flow = float('inf')
       s =sink
       while s != source:
         path_flow = min(path_flow, self.adjacency_matrix[parent[s]][s])
         s =parent[s]
         max_flow += path_flow
         v =sink
         while v != source:
           u =parent[v]
           self.adjacency_matrix[u][v]-= path_flow
           self.adjacency_matrix[v][u] += path_flow
           v =parent[v]
   return max_flow
   def bfs(self, source, sink, parent):
     visited = [False] * self.num_vertices
     queue = []
     queue.append(source)
     visited[source] = True
     while queue:
       u =queue.pop(0)
       for v in range(self.num_vertices):
         if not visited[v] and self.adjacency_matrix[u][v] > 0:
           queue.append(v)
           visited[v] = True
           parent[v] = u
     return visited[sink]
## 3. **Question:**
Given a flow network with vertices, edges, and their capacities, find the maximum flow using the Ford-Fulkerson algorithm.
### Solution:
 ```python
class Graph:
 def __init__(self, num_vertices):
   self.num_vertices = num_vertices
   self.adjacency_matrix = [[0] * num_vertices for _ in range(num_vertices)]
 def add_edge(self, src, dest, capacity):
   self.adjacency_matrix[src][dest] = capacity
 def ford_fulkerson(self, source, sink):
   parent = [-1] * self.num_vertices
   max_flow = 0
   while self.bfs(source, sink, parent):
     path_flow = float('inf')
     s =sink
     while s != source:
       path_flow = min(path_flow, self.adjacency_matrix[parent[s]][s])
       s =parent[s]
       max_flow += path_flow
       v =sink
       while v != source:
         u =parent[v]
         self.adjacency_matrix[u][v]-= path_flow
         self.adjacency_matrix[v][u] += path_flow
         v =parent[v]
   return max_flow
```
## 4. **Question:**
Given a flow network with vertices, edges, and their capacities, find the maximum flow using the Edmonds-Karp algorithm.
### Solution:
 ```python
 class Graph:
   def __init__(self, num_vertices):
     self.num_vertices = num_vertices
     self.adjacency_matrix = [[0] * num_vertices for _ in range(num_vertices)]
   def add_edge(self, src, dest, capacity):
     self.adjacency_matrix[src][dest] = capacity
   def edmonds_karp(self, source, sink):
     parent = [-1] * self.num_vertices
     max_flow = 0
     while self.bfs(source, sink, parent):
       path_flow = float('inf')
       s =sink
       while s != source:
         path_flow = min(path_flow, self.adjacency_matrix[parent[s]][s])
         s =parent[s]
         max_flow += path_flow
         v =sink
         while v != source:
           u =parent[v]
           self.adjacency_matrix[u][v]-= path_flow
           self.adjacency_matrix[v][u] += path_flow
           v =parent[v]
   return max_flow
```
## 5. **Question:**
Given a network with vertices representing tasks and edges representing dependencies, find the maximum flow that can be achieved using the Ford-Fulkerson algorithm.
### Solution:
 ```python
 class Graph:
   def __init__(self, num_vertices):
     self.num_vertices = num_vertices
     self.adjacency_matrix = [[0] * num_vertices for _ in range(num_vertices)]
   def add_edge(self, src, dest, capacity):
     self.adjacency_matrix[src][dest] = capacity
   def ford_fulkerson(self, source, sink):
     parent = [-1] * self.num_vertices
     max_flow = 0
     while self.bfs(source, sink, parent):
       path_flow = float('inf')
       s =sink
       while s != source:
         path_flow = min(path_flow, self.adjacency_matrix[parent[s]][s])
         s =parent[s]
         max_flow += path_flow
         v =sink
         while v != source:
           u =parent[v]
           self.adjacency_matrix[u][v]-= path_flow
           self.adjacency_matrix[v][u] += path_flow
           v =parent[v]
   return max_flow
```
