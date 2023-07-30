# String manipulation and pattern matching:
## 1. **Question:**
Write a function to check if a given string is a palindrome (reads the same forwards and backwards).
### Solution:
 ```python
 def is_palindrome(string):
   return string == string[::-1]
 ```
## 2. **Question:**
Given a string, write a function to find the longest palindrome substring within it.
### Solution:
 ```python
 def longest_palindrome(string):
   max_palindrome = ""
     for i in range(len(string)):
       for j in range(i, len(string)):
         substring = string[i:j+1]
         if is_palindrome(substring) and len(substring) > len(max_palindrome):
           max_palindrome = substring
   return max_palindrome
 ```
## 3. **Question:**
Write a function to count the occurrences of a pattern in a given string.
### Solution:
 ```python
def count_pattern_occurrences(string, pattern):
 count = 0
 pattern_length = len(pattern)
 for i in range(len(string)- pattern_length + 1):
   if string[i:i+pattern_length] == pattern:
     count += 1
   return count
 ```
## 4. **Question:**
Given a string, write a function to reverse the order of words in it.
### Solution:
 ```python
 def reverse_words(string):
   words = string.split()
   return " ".join(words[::-1])
 ```
## 5. **Question:**
Write a function to remove all occurrences of a pattern from a given string.
### Solution:
 ```python
 def remove_pattern(string, pattern):
   return string.replace(pattern, "")
```
