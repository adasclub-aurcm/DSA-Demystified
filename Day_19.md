# Divide and conquer paradigm
## 1. **Question:**
Write a recursive function to calculate the power of a number, given the base and exponent, using the Divide and Conquer approach.
### Solution:
 ```python
 def power(base, exponent):
   if exponent == 0:
     return 1
   elif exponent % 2 == 0:
     result = power(base, exponent // 2)
     return result * result
   else:
     result = power(base, (exponent- 1) // 2)
     return base * result * result
 # Example usage:
 base = 2
 exponent = 5
 result = power(base, exponent)
 print(f"{base} raised to the power of {exponent} is {result}")
 # Output: 2 raised to the power of 5 is 32
 ```
## 2. **Question:**
Implement the Merge Sort algorithm using the Divide and Conquer approach to sort an array of integers in ascending order.
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
       merged.extend(left[i:])
       merged.extend(right[j:])
   return merged
 # Example usage:
 input_arr = [5, 2, 8, 1, 9]
 sorted_arr = merge_sort(input_arr)
 print(sorted_arr)
 # Output: [1, 2, 5, 8, 9]
 ```
 ## 3. **Question:**
 Write a recursive function to find the maximum element in an array using the Divide and Conquer approach.
 ### Solution:
 ```python
 def find_max(arr):
   if len(arr) == 1:
     return arr[0]
   mid = len(arr) // 2
   left_max = find_max(arr[:mid])
   right_max = find_max(arr[mid:])
   return max(left_max, right_max)
 # Example usage:
 input_arr = [5, 2, 8, 1, 9]
 max_element = find_max(input_arr)
 print(f"The maximum element in the array is {max_element}")
 # Output: The maximum element in the array is 9
 ```
 ## 4. **Question:**
 Implement the Binary Search algorithm using the Divide and Conquer approach to find the index of a target element in a sorted array.
 ### Solution:
 ```python
 def binary_search(arr, target):
   low, high = 0, len(arr)- 1
   while low <= high:
   mid = (low + high) // 2
   if arr[mid] == target:
     return mid
   elif arr[mid] < target:
    low = mid + 1
   else:
     high = mid- 1
   return-1
 # Example usage:
 input_arr = [1, 2, 5, 8, 9]
 target = 5
 index = binary_search(input_arr, target)
 if index !=-1:
   print(f"The target element {target} is found at index {index}")
 else:
   print(f"The target element {target} is not found in the array")
 # Output: The target element 5 is found at index 2
 ```
## 5. **Question:**
Write a recursive function to compute the nth term of the Fibonacci sequence using the Divide and Conquer approach.
### Solution:
 ```python
 def fibonacci(n):
   if n <= 1:
     return n
   return fibonacci(n- 1) + fibonacci(n- 2)
 # Example usage:
 num=6
 result = fibonacci(num)
 print(f"The {num}th term of the Fibonacci sequence is {result}")
 # Output: The 6th term of the Fibonacci sequence is 8.
```
