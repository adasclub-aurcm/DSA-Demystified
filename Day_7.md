# Binary search and its implementation
## 1. **Question:**
Implement a binary tree node and write a function to perform an inorder traversal recursively.
### Solution:
 ```python
 class TreeNode:
   def __init__(self, data):
     self.data = data
     self.left = None
     self.right = None
   def inorder_recursive(root):
     if root:
       inorder_recursive(root.left)
       print(root.data, end=" ")
       inorder_recursive(root.right)
 ```
## 2. **Question:**
Given a binary tree, write a function to perform a preorder traversal iteratively using a stack.
### Solution:
 ```python
 class TreeNode:
   def __init__(self, data):
     self.data = data
     self.left = None
     self.right = None
   def preorder_iterative(root):
     if not root:
       return
     stack = []
     stack.append(root)
     while stack:
       node = stack.pop()
       print(node.data, end=" ")
       if node.right:
         stack.append(node.right)
       if node.left:
         stack.append(node.left)
 ```
## 3. **Question:** 
Implement a binary tree and write a function to calculate its height (maximum depth).
### Solution:
 ```python
 class TreeNode:
   def __init__(self, data):
     self.data = data
     self.left = None
     self.right = None
   def tree_height(root):
     if not root:
       return 0
     left_height = tree_height(root.left)
     right_height = tree_height(root.right)
     return max(left_height, right_height) + 1
 ```
 ## 4. **Question:**
 Given a binary tree, write a function to check if it is a valid binary search tree(BST).
 ### Solution:
 ```python
 class TreeNode:
   def __init__(self, data):
     self.data = data
     self.left = None
     self.right = None
   def is_bst(root):
     def helper(node, min_val, max_val):
       if not node:
         return True
       if node.data <= min_val or node.data >= max_val:
         return False
       return helper(node.left, min_val, node.data) and helper(node.right, node.data, max_val)
     return helper(root, float('-inf'), float('inf'))
 ```
## 5. **Question:**
Given a binary tree, write a function to find the diameter (longest path between any two nodes) of the tree.
### Solution:
 ```python
 class TreeNode:
   def __init__(self, data):
     self.data = data
     self.left = None
     self.right = None
   def tree_diameter(root):
     def height(node):
       if not node:
         return 0
       left_height = height(node.left)
       right_height = height(node.right)
       return max(left_height, right_height) + 1
     if not root:
       return 0
     left_height = height(root.left)
     right_height = height(root.right)
     left_diameter = tree_diameter(root.left)
     right_diameter = tree_diameter(root.right)
     return max(left_height + right_height, max(left_diameter, right_diameter
      ```
