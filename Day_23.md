# Bellman-Ford algorithm:
## 1. **Question:**
You are given a weighted directed graph with N vertices and M edges, including some negative weight edges. Write a function to find the shortest path from a given source vertex to a target vertex using the Bellman-Ford algorithm.
### Solution:
 ```python
 class Graph:
 def __init__(self, num_vertices):
   self.num_vertices = num_vertices
   self.edges = []
 def add_edge(self, src, dest, weight):
   self.edges.append((src, dest, weight))
 def bellman_ford(self, source, target):
   distances = [float('inf')] * self.num_vertices
   distances[source] = 0
   for _ in range(self.num_vertices- 1):
     for src, dest, weight in self.edges:
       if distances[src] != float('inf') and distances[src] + weight < distances[dest]:
         distances[dest] = distances[src] + weight
         if distances[target] == float('inf'):
           return "No path exists"
   return distances[target]
 ```
## 2. **Question:**
You are given a network of cities connected by roads with varying travel times. Write a function to find the shortest path from a given source city to all other cities using the Bellman-Ford algorithm.
### Solution:
 ```python
 class Graph:
 def __init__(self, num_cities):
   self.num_cities = num_cities
   self.roads = []
 def add_road(self, src, dest, travel_time):
   self.roads.append((src, dest, travel_time))
 def bellman_ford(self, source):
   travel_times = [float('inf')] * self.num_cities
   travel_times[source] = 0
   for _ in range(self.num_cities- 1):
     for src, dest, travel_time in self.roads:
       if travel_times[src] != float('inf') and travel_times[src] + travel_time <travel_times[dest]:
         travel_times[dest] = travel_times[src] + travel_time
   return travel_times
 ```
 ## 3. **Question:**
 You are given a flight network with airports as nodes and flight durations as edge weights. Write a function to find the shortest path from a given source airport to a target airport using the Bellman-Ford algorithm.
 ### Solution:
 ```python
 class Graph:
 def __init__(self, num_airports):
   self.num_airports = num_airports
   self.flights = []
 def add_flight(self, src, dest, duration):
   self.flights.append((src, dest, duration))
 def bellman_ford(self, source, target):
   durations = [float('inf')] * self.num_airports
   durations[source] = 0
   for _ in range(self.num_airports- 1):
     for src, dest, duration in self.flights:
       if durations[src] != float('inf') and durations[src] + duration < durations[dest]:
          durations[dest] = durations[src] + duration
       if durations[target] == float('inf'):
           return "No flight available"
   return durations[target]
 ```
## 4. **Question:**
You are given a social network with users as nodes and friendship strengths as edge weights. Write a function to find the shortest path from a given source user to a target user using the Bellman-Ford algorithm.
### Solution:
 ```python
 class Graph:
 def __init__(self, num_users):
   self.num_users = num_users
   self.friendships = []
 def add_friendship(self, user1, user2, strength):
   self.friendships.append((user1, user2, strength))
 def bellman_ford(self, source, target):
   strengths = [float('-inf')] * self.num_users
   strengths[source] = 0
   for _ in range(self.num_users- 1):
     for user1, user2, strength in self.friendships:
       if strengths[user1] != float('-inf') and strengths[user1] + strength > strengths[user2]:
         strengths[user2] = strengths[user1] + strength
       if strengths[target] == float('-inf'):
         return "No connection found"
   return strengths[target]
 ```
## 5. **Question:**
You are given a transportation network with stations as nodes and travel times as edge weights. Write a function to find the shortest path from a given source station to a target station using the Bellman-Ford algorithm.
### Solution:
 ```python
 class Graph:
 def __init__(self, num_stations):
   self.num_stations = num_stations
   self.connections = []
 def add_connection(self, station1, station2, travel_time):
   self.connections.append((station1, station2, travel_time))
 def bellman_ford(self, source, target):
   travel_times = [float('inf')] * self.num_stations
   travel_times[source] = 0
   for _ in range(self.num_stations- 1):
     for station1, station2, travel_time in self.connections:
       if travel_times[station1] != float('inf') and travel_times[station1] + travel_time < travel_times[station2]:
         travel_times[station2] = travel_times[station1] + travel_time
       if travel_times[target] == float('inf'):
         return "No connection found"
   return travel_times[target]
```
