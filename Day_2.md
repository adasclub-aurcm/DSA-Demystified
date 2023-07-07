# Big O notation and time complexity analysis
## 1 .**Question:** 
Analyze the time complexity of the following function:
### Solution:
```python
def find_duplicates(arr):
    duplicates = []
    for i in range(len(arr)):
        for j in range(i + 1, len(arr)):
            if arr[i] == arr[j]:
                duplicates.append(arr[i])
    return duplicates
```
The time complexity of this function is O(n^2), where n is the length of the input array. This is because there are nested loops, and for each element in the outer loop, the inner loop iterates through the remaining elements.

## 2 .**Question:** 
Determine the time complexity of the following code snippet:

### Solution:

```python
def print_pattern(n):
    for i in range(n):
        for j in range(i):
            print("*", end="")
        print()
```

The time complexity of this code snippet is O(n^2), where n is the input value. The outer loop runs n times, and for each iteration, the inner loop runs i times, where i increases from 0 to n-1. The total number of iterations is (n * (n - 1)) / 2, which simplifies to O(n^2).

## 3 .**Question:** 
Explain the difference between O(1), O(n), and O(n^2) time complexities and provide an example of each.

### Solution:

- O(1) represents constant time complexity. It means the algorithm's execution time does not depend on the input size. An example is accessing an element in an array by its index.
  
```python
def access_element(arr, index):
    return arr[index]
```

- O(n) represents linear time complexity. It means the algorithm's execution time grows linearly with the input size. An example is finding the maximum element in an unsorted array.
  
```python
def find_max(arr):
    max_value = arr[0]
    for i in range(1, len(arr)):
        if arr[i] > max_value:
            max_value = arr[i]
    return max_value
```

- O(n^2) represents quadratic time complexity. It means the algorithm's execution time grows quadratically with the input size. An example is finding all pairs of elements in an array.
  
```python
def find_pairs(arr):
    pairs = []
    for i in range(len(arr)):
        for j in range(i + 1, len(arr)):
            pairs.append((arr[i], arr[j]))
    return pairs
```
## 4 .**Question:**

Analyze the time complexity of the following recursive function:
### Solution:
  ``` python
def factorial(n):
    if n <= 1:
        return 1
    else:
        return n * factorial(n - 1)

```
The time complexity of this recursive function is O(n), where n is the input value. Each recursive call reduces the problem size by one, and there are n total recursive calls. The function has a linear time complexity.

## 5 .**Question:**
Analyze the time complexity of the following function:
### Solution:
``` python
def find_pairs(arr):
    pairs = []
    for i in range(len(arr)):
        for j in range(i, len(arr)):
            pairs.append((arr[i], arr[j]))
    return pairs
```
The time complexity of this function is O(n^2), where n is the length of the input array. There are nested loops, and the inner loop starts from the current value of the outer loop variable. The total number of iterations is (n * (n + 1)) / 2, which simplifies to O(n^2).
