# Arrays and their manipulation
## 1 .**Question:**
Given an array of integers, write a function to find the maximum element in the array.
### Solution:
```python
def find_max(arr):
  max_val = float('-inf')
  for num in arr:
    if num > max_val:
      max_val = num
  return max_val
```
## 2 .**Question:**
Given two sorted arrays, merge them into a single sorted array in ascending order.
### Solution:
```python
def merge_sorted_arrays(arr1, arr2):
 merged = []
 i = j = 0
 while i < len(arr1) and j < len(arr2):
  if arr1[i] <= arr2[j]:
   merged.append(arr1[i])
   i += 1
  else:
   merged.append(arr2[j])
   j += 1
# Append remaining elements
merged.extend(arr1[i:])
merged.extend(arr2[j:])
return merged
```
## 3 .**Question:**
Given an array of integers, write a function to remove all duplicates and return a
new array with unique elements.
### Solution:
```python
def remove_duplicates(arr):
 unique = []
 for num in arr:
  if num not in unique:
   unique.append(num)
return unique
```
## 4 .**Question:**
Given an array of integers, rotate the elements in the array by a given number
of positions to the right.
### Solution:
```python
def rotate_array(arr, k):
 n = len(arr)
 k = k % n # To handle k larger than array size
 rotated = arr[-k:] + arr[:-k]
 return rotated
```
## 5 .**Question:**
Given an array of integers, find the two elements that sum up to a specific
target value. Assume that there is exactly one solution
### Solution:
```python
def two_sum(arr, target):
  num_dict = {}
  for num in arr:
    complement = target - num
    if complement in num_dict:
      return [num, complement]
    num_dict[num] = True
  return None
```
