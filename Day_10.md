# Depth-First Search (DFS) algorithm :
## 1. **Question:**
Given an undirected graph, write a function to perform a depth-first traversal(DFS) starting from a given vertex.
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
Given a binary tree, write a function to perform a depth-first traversal (DFS) in pre-order.
### Solution:
 ```python
 class TreeNode:
   def __init__(self, val=0, left=None, right=None):
     self.val = val
     self.left = left
     self.right = right
 def dfs_preorder(root):
    if not root:
      return
    print(root.val, end=" ")
    dfs_preorder(root.left)
    dfs_preorder(root.right)
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
Given a maze represented as a 2D grid, write a function to find a path from the start cell to the destination cell using depth-first search (DFS).
### Solution:
 ```python
 def dfs_maze(maze, start, end):
   num_rows = len(maze)
   num_cols = len(maze[0])
   visited = [[False] * num_cols for _ in range(num_rows)]
   def dfs_helper(row, col):
     if row < 0 or row >= num_rows or col < 0 or col >= num_cols or maze[row][col] ==1 or visited[row][col]:
       return False
     visited[row][col] = True
    if (row, col) == end:
       return True
    if dfs_helper(row- 1, col) or dfs_helper(row + 1, col) or dfs_helper(row, col- 1) or dfs_helper(row, col + 1):
       return True
    return False
  return dfs_helper(start[0], start[1])
 ```
## 5. **Question:**
Given a matrix of characters and a target word, write a function to determine if the word exists in the matrix using depth-first search (DFS).
### Solution:
 ```python
 def dfs_word_search(board, word):
   num_rows = len(board)
   num_cols = len(board[0])
   visited = [[False] * num_cols for _ in range(num_rows)]
   def dfs_helper(row, col, index):
     if index == len(word):
       return True
     if row < 0 or row >= num_rows or col < 0 or col >= num_cols or board[row][col] !=word[index] or visited[row][col]:
       return False
     visited[row][col] = True
     if (
       dfs_helper(row- 1, col, index + 1)
       or dfs_helper(row + 1, col, index + 1)
       or dfs_helper(row, col- 1, index + 1)
       or dfs_helper(row, col + 1, index + 1)
       ):
           return True
     visited[row][col] = False
     return False
 for i in range(num_rows):
   for j in range(num_cols):
     if dfs_helper(i, j, 0):
       return True
 return False
 ```
