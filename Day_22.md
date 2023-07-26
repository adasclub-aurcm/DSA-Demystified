# Dijkstra's algorithm
## 1. **Question:**
You are given a weighted directed graph with N vertices and M edges. Write a function to find the shortest path from a given source vertex to a target vertex using Dijkstra's algorithm.
### Solution:
 ```python
 import heapq
   def dijkstra(graph, source, target):
     distances = {vertex: float('inf') for vertex in graph}
     distances[source] = 0
     pq = [(0, source)]
     while pq:
       current_distance, current_vertex = heapq.heappop(pq)
       if current_vertex == target:
         break
       if current_distance > distances[current_vertex]:
         continue
       for neighbor, weight in graph[current_vertex]:
         distance = current_distance + weight
         if distance < distances[neighbor]:
           distances[neighbor] = distance
           heapq.heappush(pq, (distance, neighbor))
   return distances[target]
 ```
## 2. **Question:**
You are given a network of routers, and each router is connected to other routers with varying link costs. Write a function to find the shortest path from a given source router to all other routers in the network using Dijkstra's algorithm.
### Solution:
 ```python
 import heapq
   def dijkstra(network, source):
     distances = {router: float('inf') for router in network}
     distances[source] = 0
     pq = [(0, source)]
     while pq:
       current_distance, current_router = heapq.heappop(pq)
       if current_distance > distances[current_router]:
         continue
         for neighbor, weight in network[current_router]:
           distance = current_distance + weight
         if distance < distances[neighbor]:
           distances[neighbor] = distance
         heapq.heappush(pq, (distance, neighbor))
     return distances
 ```
## 3. **Question:**
You are given a map with cities as nodes and road distances as edge weights. Write a function to find the shortest route between a given source city and a target city using Dijkstra's algorithm.
### Solution:
 ```python
 import heapq
   def dijkstra(graph, source, target):
     distances = {city: float('inf') for city in graph}
     distances[source] = 0
     pq = [(0, source)]
     while pq:
       current_distance, current_city = heapq.heappop(pq)
       if current_city == target:
         break
       if current_distance > distances[current_city]:
         continue
       for neighbor, distance in graph[current_city]:
         total_distance = current_distance + distance
       if total_distance < distances[neighbor]:
         distances[neighbor] = total_distance
         heapq.heappush(pq, (total_distance, neighbor))
   return distances[target]
## 4. **Question:**
You are given a transportation network with airports as nodes and flight distances as edge weights. Write a function to find the shortest path from a given source airport to a target airport using Dijkstra's algorithm.
### Solution:
 ```python
 import heapq
 def dijkstra(network, source, target):
   distances = {airport: float('inf') for airport in network}
   distances[source] = 0
   pq = [(0, source)]
   while pq:
     current_distance, current_airport = heapq.heappop(pq)
     if current_airport == target:
       break
     if current_distance > distances[current_airport]:
       continue
     for neighbor, distance in network[current_airport]:
       total_distance = current_distance + distance
       if total_distance < distances[neighbor]:
         distances[neighbor] = total_distance
         heapq.heappush(pq, (total_distance, neighbor))
   return distances[target]
 ```
## 5. **Question:**
You are given a social network with users as nodes and friendship strengths as edge weights. Write a function to find the shortest path from a given source user to a target user using Dijkstra's algorithm.
### Solution:
 ```python
 import heapq
 def dijkstra(network, source, target):
   distances = {user: float('inf') for user in network}
   distances[source] = 0
   pq = [(0, source)]
   while pq:
     current_distance, current_user = heapq.heappop(pq)
     if current_user == target:
       break
     if current_distance > distances[current_user]:
       continue
     for neighbor, strength in network[current_user]:
       total_distance = current_distance + strength
     if total_distance < distances[neighbor]:
       distances[neighbor] = total_distance
       heapq.heappush(pq, (total_distance, neighbor))
   return distances[target]
```
