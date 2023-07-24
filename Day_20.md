# Red-Black trees and balancing operations
## 1. **Question:**
Implement the insertion operation for a Red-Black tree.
### Solution:
 ```python
 class Node:
   def __init__(self, data):
     self.data = data
     self.color = "RED"
     self.left = None
     self.right = None
     self.parent = None
  def insert(root, data):
     node = Node(data)
     # Perform BST insertion
     if root is None:
       return node
     current = root
     while current:
       parent = current
       if node.data < current.data:
         current = current.left
       else:
         current = current.right
         node.parent = parent
       if node.data < parent.data:
         parent.left = node
       else:
         parent.right = node
       # Perform Red-Black tree balancing
       fix_insert(node)
       # Return the root of the updated tree
       while root.parent:
         root = root.parent
         return root
       def fix_insert(node):
         while node.parent and node.parent.color == "RED":
           if node.parent == node.parent.parent.left:
             uncle = node.parent.parent.right
           if uncle and uncle.color == "RED":
             node.parent.color = "BLACK"
             uncle.color = "BLACK"
             node.parent.parent.color = "RED"
             node = node.parent.parent
           else:
             if node == node.parent.right:  
               node = node.parent
               left_rotate(node)
               node.parent.color = "BLACK"
               node.parent.parent.color = "RED"
               right_rotate(node.parent.parent)
             else:
               uncle = node.parent.parent.left
               if uncle and uncle.color == "RED":
                 node.parent.color = "BLACK"
                 uncle.color = "BLACK"
                 node.parent.parent.color = "RED"
                 node = node.parent.parent
              else:
                 if node == node.parent.left:
                   node = node.parent
                   right_rotate(node)
                   node.parent.color = "BLACK"
                   node.parent.parent.color = "RED"
                   left_rotate(node.parent.parent)
 def left_rotate(node):
   right_child = node.right
   node.right = right_child.left
   if right_child.left:
     right_child.left.parent = node
     right_child.parent = node.parent
   if not node.parent:
     root = right_child
   elif node == node.parent.left:
     node.parent.left = right_child
   else:
     node.parent.right = right_child
     right_child.left = node
     node.parent = right_child
 def right_rotate(node):
   left_child = node.left
   node.left = left_child.right
   if left_child.right:
     left_child.right.parent = node
     left_child.parent = node.parent
   if not node.parent:
     root = left_child
   elif node == node.parent.left:
     node.parent.left = left_child
   else:
     node.parent.right = left_child
     left_child.right = node
     node.parent = left_child
 # Example usage:
 root = None
 root = insert(root, 5)
 root = insert(root, 2)
 root = insert(root, 8)
 root = insert(root, 1)
 root = insert(root, 9)
 ```
## 2. **Question:**
Implement the deletion operation for a Red-Black tree.
### Solution:
 ```python
 def delete(root, data):
   node = search(root, data)
   if not node:
     return root
   if not node.left or not node.right:
     delete_node = node
   else:
     delete_node = successor(node)
     if delete_node.left:
       child = delete_node.left
     else:
       child = delete_node.right
       child.parent = delete_node.parent
     if not delete_node.parent:
       root = child
     elif delete_node == delete_node.parent.left:
       delete_node.parent.left = child
     else:
       delete_node.parent.right = child
   if delete_node != node:
     node.data = delete_node.data
   if delete_node.color == "BLACK":  
     fix_delete(child)
     return root
 def fix_delete(node):
   while node != root and node.color == "BLACK":
     if node == node.parent.left:
       sibling = node.parent.right
     if sibling.color == "RED":
       sibling.color = "BLACK"
       node.parent.color = "RED"
       left_rotate(node.parent)
       sibling = node.parent.right
     if (not sibling.left or sibling.left.color == "BLACK") and (not sibling.right or
     sibling.right.color == "BLACK"):
       sibling.color = "RED"
       node = node.parent
     else:
         if not sibling.right or sibling.right.color == "BLACK":
           sibling.left.color = "BLACK"
           sibling.color = "RED"
   right_rotate(sibling)
   sibling = node.parent.right  
   sibling.color = node.parent.color
   node.parent.color = "BLACK"
   sibling.right.color = "BLACK"
   left_rotate(node.parent)
   node = root
   else:
     sibling = node.parent.left
     if sibling.color == "RED":
       sibling.color = "BLACK"
       node.parent.color = "RED"
       right_rotate(node.parent)
       sibling = node.parent.left
     if (not sibling.right or sibling.right.color == "BLACK") and (not sibling.left or
     sibling.left.color == "BLACK"):
       sibling.color = "RED"
       node = node.parent
     else:
         if not sibling.left or sibling.left.color == "BLACK":
           sibling.right.color = "BLACK"
           sibling.color = "RED"
           left_rotate(sibling)
           sibling = node.parent.left
           sibling.color = node.parent.color
           node.parent.color = "BLACK"
           sibling.left.color = "BLACK"
           right_rotate(node.parent)
           node = root
           node.color = "BLACK"
 def search(root, data):
   current = root
   while current and current.data != data:
     if data < current.data:
       current = current.left
     else:
       current = current.right
       return current
 def successor(node):
   if node.right:
     current = node.right
     while current.left:
       current = current.left
       return current
   current = node.parent
   while current and node == current.right:
     node = current
     current = current.parent
  return current
 # Example usage:
 root = delete(root, 2)
 root = delete(root, 9)
 ```
## 3. **Question:**
Implement the search operation for a Red-Black tree.
### Solution:
 ```python
 def search(root, data):
   current = root
   while current and current.data != data:
     if data < current.data:
       current = current.left
     else:
       current = current.right
   return current
 # Example usage:
 result = search(root, 8)
 if result:
   print(f"The element 8 is found in the Red-Black tree")
 else:
   print(f"The element 8 is not found in the Red-Black tree")
 ```
 ## 4. **Question:**
 Implement the minimum value operation for a Red-Black tree.
 ### Solution:
 ```python
 def find_min(root):
   current = root
   while current.left:
     current = current.left
     return current.data
 # Example usage:
 min_value = find_min(root)
 print(f"The minimum value in the Red-Black tree is {min_value}")
 ```
## 5. **Question:**
Implement the maximum value operation for a Red-Black tree.
### Solution:
```python
 def find_max(root):
   current = root
   while current.right:
     current = current.right
   return current.data
 # Example usage:
 max_value = find_max(root)
 print(f"The maximum value in the Red-Black tree is {max_value}")
```
