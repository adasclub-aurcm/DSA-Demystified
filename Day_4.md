# Linked lists and their operations
## 1 .**Question:**
Implement a singly linked list and write a function to insert a new node at the beginning.
### Solution:
```python
class Node:
   def __init__(self, data):
     self.data = data
     self.next = None
class LinkedList:
   def __init__(self):
     self.head = None
   def insert_at_beginning(self, data):
     new_node = Node(data)
     new_node.next = self.head
     self.head = new_node
 ```
## 2 .**Question:**
 Write a function to find the length of a singly linked list.
### Solution:
```python
 class Node:
   def __init__(self, data):
     self.data = data
     self.next = None
 class LinkedList:
   def __init__(self):
     self.head = None
   def length(self):
     count = 0
     curr = self.head
     while curr:
       count += 1
       curr = curr.next
     return count
 ```
## 3 .**Question:**
Implement a function to reverse a singly linked list.
### Solution:
```python
 class Node:
   def __init__(self, data):
     self.data = data
     self.next = None
 class LinkedList:
   def __init__(self):
     self.head = None
   def reverse(self):
     prev = None
     curr = self.head
     while curr:
       next_node = curr.nex
       prev = None
       curr = self.head
     while curr:
       next_node = curr.next
       curr.next = prev
       prev = curr
       curr = next_node
     self.head = prev
 ```
## 4 .**Question:**
Write a function to delete a node with a given value from a singly linked list.
### Solution:
```python
class Node:
  def __init__(self, data):
       self.data = data
       self.next = None
class LinkedList:
   def __init__(self):
     self.head = None
   def delete_node(self, value):
     curr = self.head
     if curr and curr.data == value:
       self.head = curr.next
       curr = None
       return
     prev = None
     while curr:
       if curr.data == value:
        break
       prev = curr
       curr = curr.next
     if not curr:
        return
     prev.next = curr.next
     curr = None
```
## 5 .**Question:**
Write a function to check if a linked list contains a cycle.
### Solution:
```python
 class Node:
   def __init__(self, data):
     self.data = data
     self.next = None
class LinkedList:
   def __init__(self):
     self.head = None
   def has_cycle(self):
     slow = fast = self.head
     while fast and fast.next:
       slow = slow.next
       fast = fast.next.next
       if slow == fast:
         return True
```
