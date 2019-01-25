#### ~ Check if the given number is odd or even
A number is even if it is divisible by 2 (i.e., num % 2 == 0). Otherwise, it is odd.
```
def check_odd_even(num):
    if num % 2 == 0:
        return "Even"
    else:
        return "Odd"
num = int(input("Please enter a number to check odd or even: "))
print(check_odd_even(num))
```
#### ~ Check if the given number is zero, positive or negative
 We check if the given number is equal to zero, then obviously the number is zero, if the number is greater than zero, the number is positive and if both the condition are not met, which implies that is less than 0.
 ```
 def check_sign(num):
    if num > 0:
        return "Positive"
    elif num == 0:
        return "Zero"
    else:
        return "Negative"
num = int(input("Please enter a number to check +ve, -ve or 0: "))
print(check_sign(num))
 ```
 #### ~ Largest of two numbers
 By intuition, we use if condition, if one number is greater than the second (a > b), then should print a is greater.
  ```
  def largest_of_two(a, b):
    if a > b:
        return "a is greater"
    else:
        return "b is greater"
a = int(input("Please enter first number: "))
b = int(input("Please enter second number: "))
print(largest_of_two(a, b))
 ```
#### ~ Largest of three numbers
Use and to compare multiple values.
```
def largest_of_three(a, b, c):
    if a > b and a > c:
        return "a is largest"
    elif b > c:
        return "b is largest"
    else:
        return "c is largest"
a = int(input("Please enter first number: "))
b = int(input("Please enter second number: "))
c = int(input("Please enter third number: "))
print(largest_of_three(a, b, c))
```
#### ~ Divisible by 3 and 5
Use the logical and operator.
Concepts used: Logical operator and
```
def check_divisibility(num):
    if num % 3 == 0 and num % 5 == 0:
        return "Divisible by both 3 and 5"
    else:
        return "Not divisible by both"
num = int(input("Please enter a number t check divisibility by 3 & 5: "))
print(check_divisibility(num))
```
#### ~ Grading System
Use elif to define ranges.
```
def check_grade(score):
    if score >= 90:
        return "Grade A"
    elif score >= 75:
        return "Grade B"
    elif score >= 60:
        return "Grade C"
    else:
        return "Fail"
score = int(input("Please enter a number between 0 -100 to check grade: "))
print(check_grade(score))
```
#### ~ Check Leap Year
Write a Python program that checks whether a given year is a leap year or not.  
The following rules determine if the year is a leap year:

1. If the year is divisible by 4, proceed to step 2. Otherwise, it’s not a leap year.
2. If the year is divisible by 100, proceed to step 3. Otherwise, it is a leap year.
3. If the year is divisible by 400, then it is a leap year. Otherwise, it’s not a leap year.

A year is a leap year if:
year % 4 == 0 and (year % 100 != 0 or year % 400 == 0)
Concepts used: Nested if-else, %, logical operators
```
def is_leap_year(year):
    if year % 4 == 0:
        if year % 100 != 0 or year % 400 == 0:
            return "Leap Year"
        else:
            return "Not Leap Year"
    else:
        return "Not Leap Year"
year = int(input("Please enter a year to check leap year: "))
print(is_leap_year(year))
```
#### ~ Ternary Operator for Pass/Fail

Concepts used: Ternary operator
```
def pass_or_fail(marks):
    return "Pass" if marks >= 40 else "Fail"
marks = int(input("Please enter a number less than 100: "))
print(pass_or_fail(marks))
```
#### ~ Absolute Value
If the number is negative, convert it to positive.
Concepts used: if-else
```
def absolute_value(num):
    if num < 0:
        num = -num
    return f"Absolute value is {num}"
num = int(input("Please enter a negative number: "))
print(absolute_value(num))
```
#### ~ FizzBuzz (Frequent Interview Q)

Write a Python program that takes an integer num and prints:  
  - "FizzBuzz" if the number is divisible by both 3 and 5
  - "Fizz" if the number is only divisible by 3
  - "Buzz" if the number is only divisible by 5
  - The number itself, if it is not divisible by 3 or 5
   
```
def fizz_buzz(num):
    if num % 3 == 0 and num % 5 == 0:
        return "FizzBuzz"
    elif num % 3 == 0:
        return "Fizz"
    elif num % 5 == 0:
        return "Buzz"
    else:
        return str(num)
num = int(input("Please enter a number: "))
print(fizz_buzz(num))
```
