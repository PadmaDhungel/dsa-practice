## Basic Numerical Logic
<details>
<summary>Digit Extraction and Manipulation Using % and // in Python</summary>

In most digit-based problems (like digit sum, reverse, count, etc.), we use:  
Modulo operator (% 10) to extract the rightmost digit of a number.  
Integer division (// 10) to remove the rightmost digit and reduce the number.  
These two operations are commonly used together in a while num > 0: loop to process the number digit by digit from right to left.  
Example:
For num = 1234:  
num % 10 → 4 (rightmost digit)  
num // 10 → 123 (number without last digit)  
This process repeats until num becomes 0.
</details>

### ~ Print all even numbers between 1 and N
Input: N = 10  Output: 2 4 6 8 10
```
last = int(input("Please enter the number: "))
## Regular way
for n in range(1,last+1): # should include `last` as well
    if(n % 2 == 0):
        print(n, end =" ")
# output: 2 4 6 8 10
------
## Pythonic way
for n in range(2, last+1, 2):# last is exclusive so (last+1)
    print(n, end=' ')
```
### ~ Find the sum of digits of a number (without converting to a string)
Input: 1234        Output: 10

**Logic:** Extract each digit by using modulo 10, add it to a running total, then remove the digit by integer division by 10 until the number is 0.

```
num = int(input("Please enter the number: "))
sum_digits = 0
while num > 0:
    last_digit = num % 10
    sum_digits += last_digit
    num = num // 10
print(sum_digits)
```
### ~ Reverse an integer number (without converting to string)
Input: 1234 → Output: 4321
```
num = int(input("Please enter the number: "))
rev_num = 0
while num > 0:
    last_digit = num % 10
    rev_num = rev_num * 10 + last_digit
    num =num // 10
print(rev_num)
```
### ~ Count the number of digits in a number
Input: 38291 → Output: 5
Divide the number by 10 repeatedly until it becomes zero, counting how many times you do this.
```
num = int(input("Please enter the number: "))
count = 0
while num > 0:
    count += 1
    num = num // 10
print(count)
```
### ~ Check if a number is a palindrome
Input: 121 → Output: True
```
num = int(input("Please enter the number: "))
orig_num = num
rev_num = 0
while num > 0:
    last_digit = num % 10
    rev_num = rev_num * 10 + last_digit
    num  = num //10
print(orig_num == rev_num)
```
### ~ Count how many numbers from 1 to N are divisible by 3 or 5
```
num = int(input("Please enter the number: "))
count = 0
for i in range(1, num+1):
    if ( i% 3 == 0 or i % 5 == 0):
        count += 1
print(count)
```
## Pattern Printing (Nested Loops)
### ~ Print a right-angled triangle of *  
Input: 5
Output:
```
    *
    **
    ***
    ****
    *****
```
Code:
```
num = int(input("Please enter number of rows: "))
for i in range(1, num + 6):
    print('*' * i)
```
### ~ Print a number triangle
Input: 4
Output:
```
1
12
123
1234
```
Code: 
```
num = int(input("Please enter number of rows: "))
total = 0
for i in range(1,num + 1):
    total = (total*10) + i
    print(total)
# this above fails for greater than 9
###
num = int(input("Please enter the number: "))
for i in range(1,num +1):
    for j in range(1, i+1):
        print(j, end='')
    print()
```
### ~ Print an inverted star triangle
```
Input: 4
Output:
****
***
**
*
```
Code: 
```
num = int(input("Please enter number of rows: "))
for i in range(num,0,-1):
    print('*' * i)
```
### ~ Print a multiplication table of any number
``` 
# Example for 5:
5 x 1 = 5
5 x 2 = 10
...
5 x 10 = 50
```
```
num = int(input("Enter the number for the table: "))
for i in range(1,11):
    print('{} * {} = {}'.format(i, num, num * i))
```

## Logical / Math Problems

### ~ Check if a number is a prime number
| Number | Is Prime? | Reason                        |
| ------ | --------- | ----------------------------- |
| 1      | No        | By definition                 |
| 2      | Yes       | Only divisible by 1 and 2     |
| 17     | Yes       | No divisors other than 1 & 17 |

Input: 17 → Output: Prime
```
num = int(input("Enter a number to check if it's prime: "))
if num <= 1:
    print("Not Prime")
else:
    is_prime = True
    for i in range(2, int(num ** 0.5) + 1):
        if num % i == 0:
            is_prime = False
            break
    print("Prime" if is_prime else "Not Prime")
print()
```
### ~ Find all prime numbers up to N
Input: N = 10 → Output: 2, 3, 5, 7
```
upto_num= int(input("Enter a number  to list all prime numbers up to it: "))
print(f"Prime numbers up to {upto_num}:")
for num in range(2, upto_num + 1):
    is_prime = True
    for i in range(2, int(num ** 0.5) + 1):
        if num % i == 0:
            is_prime = False
            break
    if is_prime:
        print(num, end=' ')
print("\n")
```
### ~ Print factorial of a number using a loop
Input: 5 → Output: 120
```
num = int(input("Enter a number to find its factorial: "))
fact = 1
for i in range(1, num + 1):
    fact *= i
print("Factorial:", fact, "\n")
```
### ~ Check if a number is an Armstrong number
*An n-digit number is Armstrong if:
    sum of each digit raised to the power n == the number itself
    e.g., 153 = 1³ + 5³ + 3³ = 153*
```
num = int(input("Enter a number to check if Armstrong: "))
original = num 
# Count the number of digits, this is to be raised as power
count = 0
temp = num
while temp > 0:
    count += 1
    temp = temp//10
# calculate sum of each digit raised to power of count
total = 0
temp = num
while temp > 0:
    digit = temp % 10
    total += digit ** count
    temp = temp //10
# comopare with original number
print("True") if total == original else print("False")
```
e.g. 153 = 1³ + 5³ + 3³ → Output: True
OR
you can convert the entered number into string, and get the length of the digits
```
num = int(input("Enter a number to check if Armstrong: "))
str_num = str(num)
count = len(str_num)
total = 0
for digit in str_num:
    total += int(digit) ** count
if total == num:
    print("True")
else:
    print("False")
```
### ~ Find GCD of two numbers using loops (not math.gcd)
*GCD (Greatest Common Divisor) or HCF (Highest Common Factor) is the largest positive integer that divides two or more integers without leaving a remainder.*
```
a = int(input("Enter first number: "))
b = int(input("Enter second number: "))
# Step 1: Start from the smaller of the two
min_num = min(a, b)
# Step 2: Loop from min_num down to 1
for i in range(min_num, 0, -1):
    if a % i == 0 and b % i == 0:
        print("GCD is:", i)
        break
```
There is the Euclidean idea:  
GCD(a, b) = GCD(b, a % b)  
Keep doing this until b becomes 0  
At that point, a is the GCD  
Means, we can use the second part
```
a = int(input("Enter first number: "))
b = int(input("Enter second number: "))
while b != 0:
    a = b
    b = a % b
print("GCD is:", a)
```
##  String-Based Problems

### ~ Count vowels and consonants in a string
```
input_str = input("Enter a string: ").lower()
vowels = "aeiou"
vowel_count = 0
consonant_count = 0
for ch in input_str:
    if ch.isalpha():  # only count letters
        if ch in vowels:
            vowel_count += 1
        else:
            consonant_count += 1

print("Vowels:", vowel_count)
print("Consonants:", consonant_count)
```
### ~ Reverse a string using loop (don’t use slicing)
```
input_str = input("Enter a string: ")
reversed_str = ""
for i in range(len(input_str) - 1, -1, -1):
    reversed_str += input_str[i]
print("Reversed string:", reversed_str)

```
### ~ Check if a string is a palindrome
Input: "level" → Output: True
```
string = input("Please enter word to check palindrome:")
n = len(string)
match = True
for i in range(n // 2):
    if string[i] != string[n - i - 1]:
        match=False
        break #stops checking further
print(match)
```
### ~ Find sum and average of N numbers
```
n = int(input("Enter how many numbers: "))
total = 0
i = 0
while i < n:
    num = float(input(f"Enter number {i+1}: "))
    total += num
    i += 1
average = total / n if n != 0 else 0
print("Sum:", total)
print("Average:", average)
```
### ~ Check if a number is a perfect number
*A number is perfect if the sum of its divisors (excluding itself) equals the number*  
e.g. 28 → 1 + 2 + 4 + 7 + 14 = 28
```
num = int(input("Enter a number to check if it's perfect: "))
sum_divisors = 0
i = 1
while i < num:
    if num % i == 0:
        sum_divisors += i
    i += 1
if sum_divisors == num:
    print(f"{num} is a Perfect Number.")
else:
    print(f"{num} is NOT a Perfect Number.")
```
### ~  FizzBuzz:

Take two divisors from the user that checks if the number between 1 to 30 is divisible:  
→ Print “Fizz” if divisible by first, “Buzz” if divisible by second, and “FizzBuzz” if divisible by both
```
div1 = int(input("Enter the first divisor less than 15: "))
div2 = int(input("Enter the second divisor less than 15: "))
if 0< div1 < 16 and 0 < div2 < 16: 
    for i in range(1, 31):
        if i % div1 == 0 and i % div2 == 0:
            print("FizzBuzz")
        elif i % div1 == 0:
            print("Fizz")
        elif i % div2 == 0:
            print("Buzz")
        else:
            print(i)
else:
    print("the divisors are greter than 15)
```