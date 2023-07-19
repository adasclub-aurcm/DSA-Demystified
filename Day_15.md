
# Merge Sort
## 1. **Question:**
Implement the Merge Sort algorithm to sort an array of integers in ascending order.
### Solution:
 ```python
 def merge_sort(arr):
   if len(arr) <= 1:
     return arr
   mid = len(arr) // 2
   left = merge_sort(arr[:mid])
   right = merge_sort(arr[mid:])
   return merge(left, right)
 def merge(left, right):
   merged = []
   i = j = 0
   while i < len(left) and j < len(right):
     if left[i] <= right[j]:
       merged.append(left[i])
       i += 1
     else:
       merged.append(right[j])
       j += 1
   while i < len(left):
     merged.append(left[i])
     i += 1
   while j < len(right):
     merged.append(right[j])
     j += 1
   return merged
 # Example usage:
 input_arr = [5, 2, 8, 1, 9]
 sorted_arr = merge_sort(input_arr)
 print(sorted_arr)
 # Output: [1, 2, 5, 8, 9]
 ```
 ## 2. **Question:**
 Implement the Merge Sort algorithm to sort an array of strings in lexicographic (alphabetical) order.
 ### Solution:
 ```python
 def merge_sort_strings(arr):
   if len(arr) <= 1:
     return arr
   mid = len(arr) // 2
   left = merge_sort_strings(arr[:mid])
   right = merge_sort_strings(arr[mid:])
   return merge_strings(left, right)
 def merge_strings(left, right):
   merged = []
   i = j = 0
   while i < len(left) and j < len(right):
     if left[i] <= right[j]:
       merged.append(left[i])
       i += 1
     else:
       merged.append(right[j])
       j += 1
   while i < len(left):
     merged.append(left[i])
     i += 1
   while j < len(right):
     merged.append(right[j])
     j += 1
   return merged
 # Example usage:
input_arr = ['apple', 'banana', 'cherry', 'date', 'berry']
 sorted_arr = merge_sort_strings(input_arr)
 print(sorted_arr)
 # Output: ['apple', 'banana', 'berry', 'cherry', 'date']
 ```
 ## 3. **Question:**
 Implement the Merge Sort algorithm to sort a list of objects based on a specific attribute.
 ### Solution:
 ```python
 class Person:
   def __init__(self, name, age):
     self.name = name
     self.age = age
   def merge_sort_objects(arr):
     if len(arr) <= 1:
       return arr
     mid = len(arr) // 2
     left = merge_sort_objects(arr[:mid])
     right = merge_sort_objects(arr[mid:])
     return merge_objects(left, right)
   def merge_objects(left, right):
     merged = []
     i = j = 0
     while i < len(left) and j < len(right):
       if left[i].age <= right[j].age:
         merged.append(left[i])
         i += 1
       else:
         merged.append(right[j])
         j += 1
     while i < len(left):
       merged.append(left[i])
       i += 1
     while j < len(right):
       merged.append(right[j])
       j += 1
     return merged
 # Example usage:
 person1 = Person('John', 25)
 person2 = Person('Alice', 30)
 person3 = Person('Bob', 20)
 input_arr =[person1, person2, person3]
 sorted_arr = merge_sort_objects(input_arr)
 for person in sorted_arr:
   print(person.name, person.age)
 # Output:
 # Bob 20
 # John 25
 # Alice 30
 ```
## 4. **Question:**
Implement the Merge Sort algorithm to sort an array of integers in descending order.
### Solution:
 ```python
 def merge_sort_descending(arr):
   if len(arr) <= 1:
     return arr
   mid = len(arr) // 2
   left = merge_sort_descending(arr[:mid])
   right = merge_sort_descending(arr[mid:])
   return merge_descending(left, right)
 def merge_descending(left, right):
   merged = []
   i = j = 0
   while i < len(left) and j < len(right):
     if left[i] >= right[j]:
       merged.append(left[i])
       i += 1
     else:
       merged.append(right[j])
       j += 1
   while i < len(left):
     merged.append(left[i])
     i += 1
   while j < len(right):
     merged.append(right[j])
     j += 1
   return merged
 # Example usage:
 input_arr = [5, 2, 8, 1, 9]
 sorted_arr = merge_sort_descending(input_arr)
 print(sorted_arr)
 # Output: [9, 8, 5, 2, 1]
 ```
 ## 5. **Question:**
 Implement the Merge Sort algorithm to sort a linked list in ascending order.
 ### Solution:
 ```python
 class Node:
   def __init__(self, data):
     self.data = data
     self.next = None
   def merge_sort_linked_list(head):
     if not head or not head.next:
       return head
     mid = get_middle(head)
     left = head
     right = mid.next
     mid.next = None
     left = merge_sort_linked_list(left)
     right = merge_sort_linked_list(right)
     return merge_linked_list(left, right)
   def merge_linked_list(left, right):
     dummy=Node(0)
     current = dummy
     while left and right:
       if left.data <= right.data:
         current.next = left
         left = left.next
       else:
         current.next = right
         right = right.next
         current = current.next
       if left:
         current.next = left
        if right:
         current.next = right
         return dummy.next
   def get_middle(head):
     slow = fast = head
     while fast and fast.next and fast.next.next:
       slow = slow.next
       fast = fast.next.next
       return slow
 # Example usage:
 node1 = Node(5)
 node2 = Node(2)
 node3 = Node(8)
 node4 = Node(1)
 node5 = Node(9)
 node1.next = node2
 node2.next = node3
 node3.next = node4
 node4.next = node5
 head = node1
 sorted_list = []
 current = merge_sort_linked_list(head)
   while current:
     sorted_list.append(current.data)
     current = current.next
   print(sorted_list)
 # Output: [1, 2, 5, 8, 9]
```
