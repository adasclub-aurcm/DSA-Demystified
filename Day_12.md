# Insertion sort
## 1. **Question:**
Implement the Insertion Sort algorithm to sort an array of strings in lexicographic (alphabetical) order.
### Solution:
 ```python
 def insertion_sort_strings(arr):
   for i in range(1, len(arr)):
     key = arr[i]
     j = i- 1
     while j >= 0 and arr[j] > key:
       arr[j + 1] = arr[j]
       j-= 1
       arr[j + 1] = key
     return arr
 # Example usage:
 input_arr = ['apple', 'banana', 'cherry', 'date', 'berry']
 sorted_arr = insertion_sort_strings(input_arr)
 print(sorted_arr)
 # Output: ['apple', 'banana', 'berry', 'cherry', 'date']
 ```
 ## 2. **Question:**
 Implement the Insertion Sort algorithm to sort a list of objects based on a specific attribute.
 ### Solution:
 ```python
 class Person:
   def __init__(self, name, age):
     self.name = name
     self.age = age
   def insertion_sort_objects(arr):
     for i in range(1, len(arr)):
       key = arr[i]
       j = i- 1
       while j >= 0 and arr[j].age > key.age:
         arr[j + 1] = arr[j]
         j-= 1
       arr[j + 1] = key
     return arr
# Example usage:
 person1 = Person('John', 25)
 person2 = Person('Alice', 30)
 person3 = Person('Bob', 20)
 input_arr = [person1, person2, person3]
 sorted_arr = insertion_sort_objects(input_arr, key=lambda x: x.age)
 for person in sorted_arr:
   print(person.name, person.age)
 # Output:
 # Bob 20
 # John 25
 # Alice 30
 ```
 ## 3.** Question:**
 Implement the Insertion Sort algorithm to sort an array of integers in descending order.
 ### Solution:
 ```python
 def insertion_sort_descending(arr):
   for i in range(1, len(arr)):
     key = arr[i]
     j = i- 1
     while j >= 0 and arr[j] < key:
       arr[j + 1] = arr[j]
       j-= 1
     arr[j + 1] = key
   return arr
 # Example usage:
 input_arr = [5, 2, 8, 1, 9]
 sorted_arr = insertion_sort_descending(input_arr)
 print(sorted_arr)
 # Output: [9, 8, 5, 2, 1]
 ```
## 4. **Question:**
Implement the Insertion Sort algorithm to sort a linked list in ascending order.
### Solution:
 ```python
 class Node:
   def __init__(self, data):
     self.data = data
     self.next = None
   def insertion_sort_linked_list(head):
     if not head or not head.next:
       return head
     dummy=Node(0)
     dummy.next = head
     curr = head.next
     prev_sorted = head
     while curr:
       if curr.data < prev_sorted.data:
           prev = dummy
           while prev.next.data < curr.data:
             prev = prev.next
           prev_sorted.next = curr.next
           curr.next = prev.next
           prev.next = curr
           curr = prev_sorted.next
       else:
         curr = curr.next
         prev_sorted = prev_sorted.next
 return dummy.next
 # Example usage:
 node1 = Node(5)
 node2 = Node(2)
 node3 = Node(8)
 node4.next = Node(1)
 head = node1
 sorted_head = insertion_sort_linked_list(head)
 sorted_list = []
 current = sorted_head
 while current:
   sorted_list.append(current.data)
   current = current.next
 print(sorted_list)
 # Output: [1, 2, 5, 8]
 ```
