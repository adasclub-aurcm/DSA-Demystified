# Dynamic programming: Longest Common Subsequence
## 1. **Question:**
Solve the 0/1 Knapsack problem using dynamic programming. Given a set of items with weights and values, determine the maximum value that can be obtained by selecting items such that the total weight does not exceed a given capacity.
### Solution:
```python
 def knapsack_01(weights, values, capacity):
   n =len(weights)
   dp = [[0] * (capacity + 1) for _ in range(n + 1)]
   for i in range(1, n + 1):
     for j in range(1, capacity + 1):
       if weights[i- 1] <= j:
         dp[i][j] = max(values[i- 1] + dp[i- 1][j- weights[i- 1]], dp[i- 1][j])
       else:
         dp[i][j] = dp[i- 1][j]
     return dp[n][capacity]
 ```
## 2. **Question:**
Given a list of items with weights and values, determine the minimum weight subset that can achieve a target value using the Dynamic Programming approach.
### Solution:
 ```python
 def subset_sum(weights, values, target):
   n =len(weights)
   dp = [[float('inf')] * (target + 1) for _ in range(n + 1)]
   for i in range(n + 1):
     dp[i][0] = 0
     for i in range(1, n + 1):
       for j in range(1, target + 1):
         if values[i- 1] <= j:
           dp[i][j] = min(weights[i- 1] + dp[i- 1][j- values[i- 1]], dp[i- 1][j])
         else:
           dp[i][j] = dp[i- 1][j]
     return dp[n][target]
 ```
## 3. **Question:**
Given a list of items with weights, values, and quantity limits, determine the maximum value that can be obtained by selecting items such that the total weight does not exceed a given capacity, and the quantity of each item does not exceed its limit.
### Solution:
 ```python
 def knapsack_limited(weights, values, limits, capacity):
   n =len(weights)
   dp = [[0] * (capacity + 1) for _ in range(n + 1)]
   for i in range(1, n + 1):
      for j in range(1, capacity + 1):
         for k in range(min(limits[i- 1] + 1, j // weights[i- 1] + 1)):
           dp[i][j] = max(dp[i][j], k * values[i- 1] + dp[i- 1][j- k * weights[i- 1]])
   return dp[n][capacity]
 ```
## 4. **Question:**
Given a list of items with weights and values, determine the maximum value that can be obtained by selecting items such that the total weight does not exceed a given capacity, and the sum of the weights of the selected items is as close as possible to half the capacity.
### Solution:
 ```python
 def knapsack_partition(weights, values, capacity):
   n =len(weights)
   total_sum = sum(weights)
   target = total_sum // 2
   dp = [[0] * (target + 1) for _ in range(n + 1)]
   for i in range(1, n + 1):
     for j in range(1, target + 1):
       if weights[i-1] <= j:
         dp[i][j] = max(values[i- 1] + dp[i- 1][j- weights[i- 1]], dp[i- 1][j])
       else:
         dp[i][j] = dp[i- 1][j]
   return dp[n][target]
 ```
## 5. **Question:**
Given a list of items with weights, values, and a maximum weight limit, determine the maximum value that can be obtained by selecting items such that the total weight does not exceed the limit, and the value-to-weight ratio is maximized.
### Solution:
 ```python
 def knapsack_fractional(weights, values, capacity):
   n =len(weights)
   ratios = [(values[i] / weights[i], i) for i in range(n)]
   ratios.sort(reverse=True)
   max_value = 0
   for ratio, index in ratios:
     if capacity >= weights[index]:
       max_value += values[index]
       capacity-= weights[index]
     else:
       max_value += ratio * capacity
       break
```
 return max_value
