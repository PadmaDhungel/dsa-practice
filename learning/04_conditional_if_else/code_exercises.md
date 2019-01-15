#### ~ Check if the given number is odd or even
A number is even if it is divisible by 2 (i.e., num % 2 == 0). Otherwise, it is odd.
```
num = 7
if num % 2 == 0:
    print("Even")
else:
    print("Odd")
```
#### ~ Check if the given number is zero, positive or negative
 We check if the given number is equal to zero, then obviously the number is zero, if the number is greater than zero, the number is positive and if both the condition are not met, which implies that is less than 0.
 ```
num = -5
if num > 0:
    print("Positive")
elif num == 0:
    print("Zero")
else:
    print("Negative")
 ```
 #### ~ Largest of two numbers
 By intuition, we use if condition, if one number is greater than the second (a > b), then should print a is greater.
  ```
a = 10
b = 20
if a > b:
    print("a is greater")
else:
    print("b is greater")
 ```
#### ~ Largest of three numbers
Use and to compare multiple values.
```
a = 10
b = 30
c = 20
if a > b and a > c:
    print("a is largest")
elif b > c:
    print("b is largest")
else:
    print("c is largest")
```
#### ~ Divisible by 3 and 5
Use the logical and operator.
Concepts used: Logical operator and
```
num = 15
if num % 3 == 0 and num % 5 == 0:
    print("Divisible by both 3 and 5")
else:
    print("Not divisible by both")
```
#### ~ Grading System
Use elif to define ranges.
```
score = 85
if score >= 90:
    print("Grade A")
elif score >= 75:
    print("Grade B")
elif score >= 60:
    print("Grade C")
else:
    print("Fail")
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
year = 2024
if year % 4 == 0:
    if year % 100 != 0 or year % 400 == 0:
        print("Leap Year")
    else:
        print("Not Leap Year")
else:
    print("Not Leap Year")
```
#### ~ Ternary Operator for Pass/Fail

Concepts used: Ternary operator
```
marks = 45
result = "Pass" if marks >= 40 else "Fail"
print(result)
```
#### ~ Absolute Value
If the number is negative, convert it to positive.
Concepts used: if-else
```
num = -10
if num < 0:
    num = -num
print("Absolute value is", num)
```
#### ~ FizzBuzz (Frequent Interview Q)

Write a Python program that takes an integer num and prints:  
  - "FizzBuzz" if the number is divisible by both 3 and 5
  - "Fizz" if the number is only divisible by 3
  - "Buzz" if the number is only divisible by 5
  - The number itself, if it is not divisible by 3 or 5
   
```
num = 15
if num % 3 == 0 and num % 5 == 0:
    print("FizzBuzz")
elif num % 3 == 0:
    print("Fizz")
elif num % 5 == 0:
    print("Buzz")
else:
    print(num)
```
