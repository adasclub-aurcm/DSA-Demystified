# Selection sort 
## 1. **Question:**
Implement the Selection Sort algorithm to sort an array of integers in ascending order.
### Solution:
 ```python
 def selection_sort(arr):
   for i in range(len(arr)):
     min_index = i
     for j in range(i + 1, len(arr)):
       if arr[j] < arr[min_index]:
         min_index = j
     arr[i], arr[min_index] = arr[min_index], arr[i]
   return arr
 # Example usage:
 input_arr = [5, 2, 8, 1, 9]
 sorted_arr = selection_sort(input_arr)
 print(sorted_arr)
 # Output: [1, 2, 5, 8, 9]
 ```
 ## 2. **Question:**
 Implement the Selection Sort algorithm to sort an array of strings in lexicographic (alphabetical) order.
 ### Solution:
 ```python
 def selection_sort_strings(arr):
   for i in range(len(arr)):
     min_index = i
     for j in range(i + 1, len(arr)):
       if arr[j] < arr[min_index]:
         min_index = j
     arr[i], arr[min_index] = arr[min_index], arr[i]
   return arr
 # Example usage:
 input_arr = ['apple', 'banana', 'cherry', 'date', 'berry']
 sorted_arr = selection_sort_strings(input_arr)
 print(sorted_arr)
 # Output: ['apple', 'banana', 'berry', 'cherry', 'date']
 ```
## 3. **Question:**
Implement the Selection Sort algorithm to sort a list of objects based on a specific attribute.
### Solution:
 ```python
class Person:
  def __init__(self, name, age):
     self.name = name
     self.age = age
  def selection_sort_objects(arr):
     for i in range(len(arr)):
       min_index = i
         for j in range(i + 1, len(arr)):
           if arr[j].age < arr[min_index].age:
             min_index = j
         arr[i], arr[min_index] = arr[min_index], arr[i]
     return arr
 # Example usage:
 person1 = Person('John', 25)
 person2 = Person('Alice', 30)
 person3 = Person('Bob', 20)
 input_arr = [person1, person2, person3]
 sorted_arr = selection_sort_objects(input_arr, key=lambda x: x.age)
 for person in sorted_arr:
   print(person.name, person.age)
 # Output:
 # Bob 20
 # John 25
 # Alice 30
 ```
 ## 4. **Question:**
 Implement the Selection Sort algorithm to sort an array of integers in descending order.
 ### Solution:
 ```python
 def selection_sort_descending(arr):
   for i in range(len(arr)):
     max_index = i
     for j in range(i + 1, len(arr)):
       if arr[j] > arr[max_index]:
         max_index = j
     arr[i], arr[max_index] = arr[max_index], arr[i]
   return arr
 # Example usage:
 input_arr = [5, 2, 8, 1, 9]
 sorted_arr = selection_sort_descending(input_arr)
 print(sorted_arr)
 # Output: [9, 8, 5, 2, 1]
 ```
## 5. **Question:**
Implement the Selection Sort algorithm to sort a linked list in ascending order.
### Solution:
 ```python
 class Node:
   def __init__(self, data):
     self.data = data
     self.next = None
   def selection_sort_linked_list(head):
     if not head or not head.next:
       return head
     current = head
     while current:
       min_node = current
       min_prev = None
       temp = current.next
       prev_temp = current
       while temp:
         if temp.data < min_node.data:
           min_node = temp
           min_prev = prev_temp
           prev_temp = temp
           temp = temp.next
         if min_node != current:
           if min_prev:
             min_prev.next = current
           else:
             head = current
             temp = current.next
             current.next = min_node.next
             min_node.next = temp
             current = current.next
   return head
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
 current = selection_sort_linked_list(head)
 while current:
   sorted_list.append(current.data)
   current = current.next
 print(sorted_list)
 # Output: [1, 2, 5, 8, 9]
```
