# Quick sort
## 1. **Question:**
Implement the Quick Sort algorithm to sort an array of integers in ascending order.
### Solution:
 ```python
 def quick_sort(arr):
   if len(arr) <= 1:
     return arr
   pivot = arr[len(arr) // 2]
   left = [x for x in arr if x < pivot]
   middle = [x for x in arr if x == pivot]
   right = [x for x in arr if x > pivot]
   return quick_sort(left) + middle + quick_sort(right)
 # Example usage:
 input_arr = [5, 2, 8, 1, 9]
 sorted_arr = quick_sort(input_arr)
 print(sorted_arr)
 # Output: [1, 2, 5, 8, 9]
 ```
## 2. **Question:**
Implement the Quick Sort algorithm to sort an array of strings in lexicographic (alphabetical) order.
### Solution:
 ```python
 def quick_sort_strings(arr):
   if len(arr) <= 1:
     return arr
   pivot = arr[len(arr) // 2]
   left = [x for x in arr if x < pivot]
   middle = [x for x in arr if x == pivot]
   right = [x for x in arr if x > pivot]
   return quick_sort_strings(left) + middle + quick_sort_strings(right)
 # Example usage:
 input_arr = ['apple', 'banana', 'cherry', 'date', 'berry']
 sorted_arr = quick_sort_strings(input_arr)
 print(sorted_arr)
 # Output: ['apple', 'banana', 'berry', 'cherry', 'date']
 ```
 ## 3. **Question:**
 Implement the Quick Sort algorithm to sort a list of objects based on a specific attribute.
 ### Solution:
 ```python
 class Person:
   def __init__(self, name, age):
     self.name = name
     self.age = age
   def quick_sort_objects(arr):
     if len(arr) <= 1:
        return arr
     pivot = arr[len(arr) // 2]
     left = [x for x in arr if x.age < pivot.age]
     middle = [x for x in arr if x.age == pivot.age]
     right = [x for x in arr if x.age > pivot.age]
     return quick_sort_objects(left) + middle + quick_sort_objects(right)
 # Example usage:
 person1 = Person('John', 25)
 person2 = Person('Alice', 30)
 person3 = Person('Bob', 20)
 input_arr = [person1, person2, person3]
 sorted_arr = quick_sort_objects(input_arr)
 for person in sorted_arr:
   print(person.name, person.age)
 # Output:
 # Bob 20
 # John 25
 # Alice 30
 ```
 ## 4. **Question:**
 Implement the Quick Sort algorithm to sort an array of integers in descending order.
 ### Solution:
 ```python
 def quick_sort_descending(arr):
   if len(arr) <= 1:
     return arr
   pivot = arr[len(arr) // 2]
   left = [x for x in arr if x > pivot]
   middle = [x for x in arr if x == pivot]
   right = [x for x in arr if x < pivot]
   return quick_sort_descending(left) + middle + quick_sort_descending(right)
 # Example usage:
 input_arr = [5, 2, 8, 1, 9]
 sorted_arr = quick_sort_descending(input_arr)
 print(sorted_arr)
 # Output: [9, 8, 5, 2, 1]
 ```
## 5. **Question:**
Implement the Quick Sort algorithm to sort a linked list in ascending order.
### Solution:
 ```python
 class Node:
   def __init__(self, data):
     self.data = data
     self.next = None
   def quick_sort_linked_list(head):
     if not head or not head.next:
       return head
     pivot = head
     current = head.next
     smaller_head = smaller_tail = None
     equal_head = equal_tail = pivot
     greater_head = greater_tail = None
     while current:
       if current.data < pivot.data:
         if smaller_head is None:
             smaller_head = current
             smaller_tail = current
         else:
           smaller_tail.next = current
           smaller_tail = smaller_tail.next
       elif current.data == pivot.data:
           equal_tail.next = current
           equal_tail = equal_tail.next
       else:
           if greater_head is None:
             greater_head = current
             greater_tail = current
           else:
             greater_tail.next = current
             greater_tail = greater_tail.next
             current = current.next
     if smaller_tail:
       smaller_tail.next = None
       smaller_head = quick_sort_linked_list(smaller_head)
       smaller_tail = smaller_head
       while smaller_tail.next:
         smaller_tail = smaller_tail.next
         smaller_tail.next = equal_head
     else:
       smaller_head = equal_head
       if greater_tail:
         greater_tail.next = None
         greater_head = quick_sort_linked_list(greater_head)
         equal_tail.next = greater_head
       else:
         equal_tail.next = None
         return smaller_head
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
 current = quick_sort_linked_list(head)
   while current:
     sorted_list.append(current.data)
     current = current.next
 print(sorted_list)
 # Output: [1, 2, 5, 8, 9]
```
