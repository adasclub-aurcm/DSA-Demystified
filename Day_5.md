# Stack, queues and their applications
## 1. **Question:** 
Implement a stack using an array and write a function to check if it is empty.
### Solution:
 ```python
 class Stack:
   def __init__(self):
     self.items = []
   def is_empty(self):
     return len(self.items) == 0
 ```
## 2. **Question:**
Implement a queue using a linked list and write a function to enqueue an element.
### Solution:
 ```python
 class Node:
   def __init__(self, data):
     self.data = data
     self.next = None
 class Queue:
   def __init__(self):
     self.head = None
     self.tail = None
  def enqueue(self, data):
     new_node = Node(data)
     if not self.head:
       self.head = new_node
       self.tail = new_node
     else:
       self.tail.next = new_node
       self.tail = new_node
```
 ## 3. **Question:**
 Given a string of parentheses, write a function to check if the parentheses are balanced using a stack.
 ### Solution:
 ```python
 def is_balanced(parentheses):
   stack = []
   opening = ['(', '[', '{']
   closing = [')', ']', '}']
   for char in parentheses:
     if char in opening:
       stack.append(char)
     elif char in closing:
       if not stack or opening.index(stack.pop()) != closing.index(char):
         return False
   return len(stack) == 0
 ```
## 4. **Question:**
Implement a queue using two stacks and write functions for enqueue and dequeue operations.
### Solution:
 ```python
 class Queue:
   def __init__(self):
     self.in_stack = []
     self.out_stack = []
   def enqueue(self, data):
     self.in_stack.append(data)
   def dequeue(self):
     if not self.out_stack:
       while self.in_stack:
         self.out_stack.append(self.in_stack.pop())
     if self.out_stack:
        return self.out_stack.pop()
     else:
        return None
 ```
## 5. **Question:**
Implement a stack that supports a min() function, which returns the minimum element in constant time.
### Solution:
 ```python
 class MinStack:
   def __init__(self):
     self.stack = []
     self.min_stack = []
   def push(self, data):
     self.stack.append(data)
     if not self.min_stack or data <= self.min_stack[-1]:
       self.min_stack.append(data)
   def pop(self):
     if self.stack:
       popped = self.stack.pop()
       if popped == self.min_stack[-1]:
         self.min_stack.pop()
       return popped
     else:
       return None
   def min(self):
     if self.min_stack:
       return self.min_stack[-1]
     else:
       return None
```
