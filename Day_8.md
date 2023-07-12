# Hashing and hash tables
## 1. **Question:**
Implement a hash table using an array and handle collisions using chaining (linked lists).
### Solution:
 ```python
 class ListNode:
   def __init__(self, key, value):
     self.key = key
     self.value = value
     self.next = None
 class HashTable:
   def __init__(self, size):
     self.size = size
     self.table = [None] * size
   def hash_function(self, key):
     return hash(key) % self.size
   def put(self, key, value):
     index = self.hash_function(key)
     if self.table[index] is None:
       self.table[index] = ListNode(key, value)
     else:
       curr = self.table[index]
       while curr.next:
         curr = curr.next
       curr.next = ListNode(key, value)
   def get(self, key):
     index = self.hash_function(key)
     curr = self.table[index]
     while curr:
       if curr.key == key:
         return curr.value
       curr = curr.next
     return None
 ```
## 2. **Question:**
Given an array of integers, find two numbers that add up to a specific target using a hash table.
### Solution:
 ```python
 def two_sum(nums, target):
   hash_table = {}
     for i, num in enumerate(nums):
       complement = target- num
       if complement in hash_table:
         return [hash_table[complement], i]
       hash_table[num] = i
     return []
 ```
 ## 3. **Question:**
Given a list of strings, group the anagrams together using a hash table.
### Solution:
 ```python
 def group_anagrams(strs):
   hash_table = {}
   for s in strs:
     sorted_s = ''.join(sorted(s))
     if sorted_s in hash_table:
       hash_table[sorted_s].append(s)
     else:
       hash_table[sorted_s] = [s]
   return list(hash_table.values())
 ```
## 4. **Question:**
Design a hash set data structure using a hash table to support insert, remove, and contains operations.
### Solution:
 ```python
class MyHashSet:
  def __init__(self):
    self.size = 1000
    self.buckets = [None] * self.size
  def hash_function(self, key):
    return key % self.size
  def add(self, key):
   index = self.hash_function(key)
   if self.buckets[index] is None:
     self.buckets[index] = [key]
   else:
     if key not in self.buckets[index]:
       self.buckets[index].append(key)
   def remove(self, key):
     index = self.hash_function(key)
     if self.buckets[index] is not None:
       if key in self.buckets[index]:
         self.buckets[index].remove(key)
   def contains(self, key):
     index = self.hash_function(key)
     if self.buckets[index] is not None:
       return key in self.buckets[index]
     return False
 ```
## 5. **Question:**
Given two lists of integers, find the intersection (common elements) using a hash table.
### Solution:
 ```python
 def intersection(nums1, nums2):
   set1 = set(nums1)
   set2 = set(nums2)
   return list(set1 & set2)
```
