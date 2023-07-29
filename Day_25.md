# Minimum Spanning Tree (MST)
## 1. **Question:**
Implement Kruskal's algorithm to find the Minimum Spanning Tree of a given weighted graph.
### Solution:
 ```python
 class Graph:
   def __init__(self, vertices):
     self.V = vertices
     self.edges = []
   def add_edge(self, src, dest, weight):
     self.edges.append((src, dest, weight))
   def find(self, parent, i):
     if parent[i] == i:
       return i
   return self.find(parent, parent[i])
   def union(self, parent, rank, x, y):
     x_root = self.find(parent, x)
     y_root = self.find(parent, y)
     if rank[x_root] < rank[y_root]:
       parent[x_root] = y_root
     elif rank[x_root] > rank[y_root]:
       parent[y_root] = x_root
     else:
       parent[y_root] = x_root
       rank[x_root] += 1
   def kruskal_mst(self):
     result = []
     self.edges.sort(key=lambda x: x[2])
     parent = [i for i in range(self.V)]
     rank = [0] * self.V
     i = 0
     e =0
     while e < self.V- 1:
       src, dest, weight = self.edges[i]
       i += 1
       x =self.find(parent, src)  
       y =self.find(parent, dest)
       if x != y:
         e += 1
         result.append((src, dest, weight))
         self.union(parent, rank, x, y)
     return result
 ```
 ## 2. **Question:**
 Implement Prim's algorithm to find the Minimum Spanning Tree of a given weighted graph.
 ### Solution:
 ```python
 class Graph:
   def __init__(self, vertices):
     self.V = vertices
     self.adjacency_matrix = [[0] * vertices for _ in range(vertices)]
   def add_edge(self, src, dest, weight):
     self.adjacency_matrix[src][dest] = weight
     self.adjacency_matrix[dest][src] = weight
   def prim_mst(self):
     key = [float('inf')] * self.V
     parent = [None] * self.V
     key[0] = 0
     mst_set = [False] * self.V
     for _ in range(self.V):
       min_key = float('inf')
       min_index =-1
     for v in range(self.V):
       if not mst_set[v] and key[v] < min_key:
         min_key = key[v]
         min_index = v
         mst_set[min_index] = True
       for v in range(self.V):
         if (self.adjacency_matrix[min_index][v] > 0 and not mst_set[v] and self.adjacency_matrix[min_index][v] < key[v]):
             key[v] = self.adjacency_matrix[min_index][v]
             parent[v] = min_index
             result = []
     for i in range(1, self.V):
       result.append((parent[i], i, self.adjacency_matrix[i][parent[i]]))
     return result
 ```
 ## 3. **Question:**
 Given a weighted graph, find the minimum weight required to connect all vertices using the MST algorithm.
 ### Solution:
 ```python
 class Graph:
   def __init__(self, vertices):
     self.V = vertices
     self.adjacency_matrix = [[0] * vertices for _ in range(vertices)]
   def add_edge(self, src,dest, weight):
     self.adjacency_matrix[src][dest] = weight
     self.adjacency_matrix[dest][src] = weight
   def min_weight_to_connect(self):
     key = [float('inf')] * self.V
     parent = [None] * self.V
     key[0] = 0
     mst_set = [False] * self.V
     min_weight = 0
     for _ in range(self.V):
       min_key = float('inf')
       min_index =-1
     for v in range(self.V):
       if not mst_set[v] and key[v] < min_key:
         min_key = key[v]
         min_index = v
         mst_set[min_index] = True
         min_weight += min_key
         for v in range(self.V):  
          if (self.adjacency_matrix[min_index][v] > 0 and not mst_set[v] and self.adjacency_matrix[min_index][v] < key[v] ):
             key[v] = self.adjacency_matrix[min_index][v]
             parent[v] = min_index
     return min_weight
 ```
 ## 4. **Question:**
 Given a weighted graph, find the edges that belong to the Minimum Spanning Tree using Kruskal's algorithm.
 ### Solution:
 ```python
 class Graph:
   def __init__(self, vertices):
     self.V = vertices
     self.edges = []
   def add_edge(self, src, dest, weight):
     self.edges.append((src, dest, weight))
   def find(self, parent, i):
     if parent[i] == i:
       return i
   return self.find(parent, parent[i])
   def union(self, parent, rank, x, y):
     x_root = self.find(parent, x)
     y_root = self.find(parent, y)
     if rank[x_root] < rank[y_root]:
       parent[x_root] = y_root
     elif rank[x_root] > rank[y_root]:
       parent[y_root] = x_root
     else:
       parent[y_root] = x_root
       rank[x_root] += 1
   def kruskal_mst_edges(self):
     result = []
     self.edges.sort(key=lambda x: x[2])
     parent = [i for i in range(self.V)]
     rank = [0] * self.V
     i = 0
     e =0
     while e < self.V- 1:
       src, dest, weight = self.edges[i]
       i += 1
       x =self.find(parent, src)
       y =self.find(parent, dest)
       if x != y:
         e += 1
         result.append((src, dest, weight))
         self.union(parent, rank, x, y)
     return result
 ```
## 5. **Question:**
Given a weighted graph, find the edges that belong to the Minimum SpanningTree using Prim's algorithm.
### Solution:
 ```python
 class Graph:
   def __init__(self, vertices):
     self.V = vertices
     self.adjacency_matrix = [[0] * vertices for _ in range(vertices)]
   def add_edge(self, src, dest, weight):
     self.adjacency_matrix[src][dest] = weight
     self.adjacency_matrix[dest][src] = weight
   def prim_mst_edges(self):
     key = [float('inf')] * self.V
     parent = [None] * self.V
     key[0] = 0
     mst_set = [False] * self.V
     result = []
     for _ in range(self.V):
       min_key = float('inf')
       min_index =1
     for v in range(self.V):
       if not mst_set[v] and key[v] < min_key:
         min_key = key[v]
         min_index = v
         mst_set[min_index] = True
      for v in range(self.V):
         if (self.adjacency_matrix[min_index][v] > 0 and not mst_set[v] and self.adjacency_matrix[min_index][v] < key[v] ):
           key[v] = self.adjacency_matrix[min_index][v]
           parent[v] = min_index
           if parent[min_index] is not None:
                result.append((parent[min_index], min_index,
                self.adjacency_matrix[min_index][parent[min_index]]))
   return result
```
