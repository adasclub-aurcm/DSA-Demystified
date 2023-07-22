# Greedy algorithms and their applications
## 1. **Question:**
You have a collection of coins of different denominations and an amount of money. Write a function to find the minimum number of coins needed to make up that amount using a greedy algorithm.
### Solution:
 ```python
 def coin_change(coins, amount):
   coins.sort(reverse=True)
   count = 0
   for coin in coins:
     count += amount // coin
     amount %= coin
   if amount > 0:
     return-1 # Not possible to make exact change
   return count
 # Example usage:
 coins = [1, 5, 10, 25]
 amount = 48
 result = coin_change(coins, amount)
 print(f"The minimum number of coins needed to make {amount} cents is {result}")
 # Output: The minimum number of coins needed to make 48 cents is 6
 ```
## 2. **Question:**
You are given a set of activities with their start and end times. Write a function to find the maximum number of activities that can be performed, assuming a person can only work on one activity at a time, using a greedy algorithm.
### Solution:
 ```python
 def max_activities(activities):
   activities.sort(key=lambda x: x[1]) # Sort by end time
   selected = [activities[0]]
   for i in range(1, len(activities)):
     if activities[i][0] >= selected[-1][1]:
       selected.append(activities[i])
   return len(selected)
 # Example usage:
 activities = [(1, 4), (3, 5), (0, 6), (5, 7), (3, 9), (5, 9), (6, 10), (8, 11), (8, 12), (2, 14), (12, 16)]
 result = max_activities(activities)
 print(f"The maximum number of activities that can be performed is {result}")
 # Output: The maximum number of activities that can be performed is 4
 ```
## 3. **Question:**
You are given a collection of intervals representing start and end times of meetings. Write a function to find the minimum number of meeting rooms required, assuming a room can only host one meeting at a time, using a greedy algorithm.
### Solution:
 ```python
 def min_meeting_rooms(intervals):
   start_times = sorted([interval[0] for interval in intervals])
   end_times = sorted([interval[1] for interval in intervals])
   rooms = 0
   end_ptr = 0
   for start in start_times:
     if start < end_times[end_ptr]:
       rooms += 1
     else:
       end_ptr += 1
   return rooms
 # Example usage:
 intervals = [(0, 30), (5, 10), (15, 20)]
 result = min_meeting_rooms(intervals)
 print(f"The minimum number of meeting rooms required is {result}")
 # Output: The minimum number of meeting rooms required is 2
 ```
## 4. **Question:**
You are given a set of items with their weights and values. Write a function to find the maximum value of items that can be packed into a knapsack of limited capacity, using a greedy algorithm.
### Solution:
 ```python
 def knapsack(capacity, items):
   items.sort(key=lambda x: x[1] / x[0], reverse=True) # Sort by value-to-weight ratio
   max_value = 0
   for item in items:
     if capacity >= item[0]:
       max_value += item[1]
       capacity-= item[0]
     else:
       max_value += item[1] * (capacity / item[0])
       break
   return max_value
 # Example usage:
 items = [(2, 10), (3, 5), (5, 15), (7, 7), (1, 6)]
 capacity = 10
 result = knapsack(capacity, items)
 print(f"The maximum value that can be packed into the knapsack is {result}")
 # Output: The maximum value that can be packed into the knapsack is 40
 ```
## 5. **Question:**
You are given a collection of intervals representing start and end times of tasks. Write a function to find the minimum number of resources required to execute all tasks without overlapping, using a greedy algorithm.
### Solution:
 ```python
 def min_resources(intervals):
   intervals.sort(key=lambda x: x[0]) # Sort by start time
   resources = [intervals[0][1]]
   for i in range(1, len(intervals)):
     allocated = False
     for j in range(len(resources)):
       if intervals[i][0] >= resources[j]:
         resources[j] = intervals[i][1]
         allocated = True
         break
       if not allocated:
         resources.append(intervals[i][1])
         return len(resources)
# Example usage:
 intervals = [(1, 4), (2, 5), (4, 7), (6, 8), (7, 9)]
 result = min_resources(intervals)
 print(f"The minimum number of resources required is {result}")
 # Output: The minimum number of resources required is 3.
```
