# Heap data structure and heap sort
## 1. **Question:**
Implement the Heap data structure with operations for insertion, deletion, and finding the minimum element.
### Solution:
 ```python
 class MinHeap:
   def __init__(self):
     self.heap = []
   def insert(self, value):
     self.heap.append(value)
     self._heapify_up(len(self.heap)- 1)
   def delete_min(self):
     if not self.heap:
       return None
     min_value = self.heap[0]
     last_value = self.heap.pop()
     if self.heap:
       self.heap[0] = last_value
       self._heapify_down(0)
       return min_value
   def find_min(self):
     return self.heap[0] if self.heap else None
   def _heapify_up(self, index):
     parent_index = (index- 1) // 2
     if parent_index >= 0 and self.heap[parent_index] > self.heap[index]:
       self.heap[parent_index], self.heap[index] = self.heap[index],
       self.heap[parent_index]
       self._heapify_up(parent_index)
   def _heapify_down(self, index):
      left_child_index = 2 * index + 1
      right_child_index = 2 * index + 2
      smallest = index
      if left_child_index < len(self.heap) and self.heap[left_child_index] < self.heap[smallest]:
         smallest = left_child_index
      if right_child_index < len(self.heap) and self.heap[right_child_index] < self.heap[smallest]:
         smallest = right_child_index
      if smallest != index:
         self.heap[index], self.heap[smallest] = self.heap[smallest], self.heap[index]
         self._heapify_down(smallest)
 ```
 ## 2. **Question:**
 Implement the Heap Sort algorithm to sort an array of integers in ascending order.
 ### Solution:
 ```python
 def heap_sort(arr):
   n =len(arr)
   for i in range(n // 2- 1,-1,-1):
     heapify(arr, n, i)
   for i in range(n- 1, 0,-1):
     arr[0], arr[i] = arr[i], arr[0]
 heapify(arr, i, 0)
 def _heapify(arr, n, i):
   largest = i
   left = 2 * i + 1
   right = 2 * i + 2
   if left < n and arr[left] > arr[largest]:
     largest = left
   if right < n and arr[right] > arr[largest]:
     largest = right
   if largest != i:
     arr[i], arr[largest] = arr[largest], arr[i]
     heapify(arr, n, largest)
 ```
 ## 3. **Question:**
 Given an array of integers, find the kth largest element using a Heap.
 ### Solution:
```python
 import heapq
 def find_kth_largest(nums, k):
   min_heap = []
   for num in nums:
     heapq.heappush(min_heap, num)
     if len(min_heap) > k:
       heapq.heappop(min_heap)
     return min_heap[0]
 ```
 ## 4. **Question:**
 Given an array of integers, find the kth smallest element using a Heap.
 ### Solution:
 ```python
 import heapq
 def find_kth_smallest(nums, k):
   max_heap = []
   for num in nums:
     heapq.heappush(max_heap,-num)
     if len(max_heap) > k:
       heapq.heappop(max_heap)
   return-max_heap[0]
 ```
 ## 5. **Question:**
 Given a list of students with their names and scores, find the top k students with the highest scores using a Heap.
 ### Solution:
 ```python
 import heapq
 class Student:
   def __init__(self, name, score):
     self.name = name
     self.score = score
   def __lt__(self, other):
     return self.score > other.score
   def find_top_k_students(students, k):
     top_students = []
   for student in students:
     heapq.heappush(top_students, student)
     if len(top_students) > k:
       heapq.heappop(top_students)
       return [student.name for student in top_students
```
