# Recursion and recursive algorithms
## 1. **Question:**
Write a recursive function to calculate the factorial of a positive integer.
### Solution:
 ```python
 def factorial(n):
   if n == 0:
     return 1
   return n * factorial(n- 1)
 # Example usage:
 num=5
 result = factorial(num)
 print(f"The factorial of {num} is {result}")
# Output: The factorial of 5 is 120
 ```
## 2. **Question:**
Write a recursive function to calculate the nth Fibonacci number.
### Solution:
 ```python
 def fibonacci(n):
   if n <= 1:
     return n
   return fibonacci(n- 1) + fibonacci(n- 2)
 # Example usage:
 num=6
 result = fibonacci(num)
 print(f"The {num}th Fibonacci number is {result}")
 # Output: The 6th Fibonacci number is 8
 ```
## 3. **Question:**
Write a recursive function to reverse a string.
### Solution:
 ```python
 def reverse_string(s):
   if len(s) <= 1:
     return s
   return reverse_string(s[1:]) + s[0]
 # Example usage:
 string = "Hello, World!"
 result = reverse_string(string)
 print(f"The reversed string is: {result}")
 # Output: The reversed string is: !dlroW ,olleH
 ```
## 4. **Question:**
Write a recursive function to find the sum of digits in a positive integer.
### Solution:
 ```python
 def sum_of_digits(n):
   if n < 10:
     return n
   return n % 10 + sum_of_digits(n // 10)
 # Example usage:
 num=12345
 result = sum_of_digits(num)
 print(f"The sum of digits in {num} is {result}")
# Output: The sum of digits in 12345 is 15
 ```
## 5. **Question:**
Write a recursive function to find the greatest common divisor (GCD) of two positive integers.
### Solution:
 ```python
 def gcd(a, b):
   if b == 0:
     return a
   return gcd(b, a % b)
 # Example usage:
 num1 =36
 num2 =48
 result = gcd(num1, num2)
 print(f"The GCD of {num1} and {num2} is {result}")
 # Output: The GCD of 36 and 48 is 12
```
