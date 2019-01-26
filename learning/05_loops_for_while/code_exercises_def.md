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
def print_even_numbers(last):
    ## Regular way
    for n in range(1, last + 1):  # should include `last` as well
        if n % 2 == 0:
            print(n, end=" ")
last = int(input("Please enter the number: "))
print_even_numbers(last)
# output: 2 4 6 8 10
------
## Pythonic way
def print_even_numbers(last):
    for n in range(2, last+1, 2):# last is exclusive so (last+1)
        print(n, end=' ')
last = int(input("Please enter the number: "))
print_even_numbers(last)
```
### ~ Find the sum of digits of a number (without converting to a string)
Input: 1234        Output: 10

**Logic:** Extract each digit by using modulo 10, add it to a running total, then remove the digit by integer division by 10 until the number is 0.

```
def sum_of_digits(num):
    sum_digits = 0
    while num > 0:
        last_digit = num % 10
        sum_digits += last_digit
        num = num // 10
    return sum_digits
num = int(input("Please enter the number: "))
print(sum_of_digits(num))
```
### ~ Reverse an integer number (without converting to string)
Input: 1234 → Output: 4321
```
def reverse_number(num):
    rev_num = 0
    while num > 0:
        last_digit = num % 10
        rev_num = rev_num * 10 + last_digit
        num =num // 10
    return rev_num
num = int(input("Please enter the number: "))
print(reverse_number(num))
```
### ~ Count the number of digits in a number
Input: 38291 → Output: 5
Divide the number by 10 repeatedly until it becomes zero, counting how many times you do this.
```
def count_digits(num):
    count = 0
    while num > 0:
        count += 1
        num = num // 10
    return count
num = int(input("Please enter the number: "))
print(count_digits(num))
```
### ~ Check if a number is a palindrome
Input: 121 → Output: True
```
def is_palindrome(num):
    orig_num = num
    rev_num = 0
    while num > 0:
        last_digit = num % 10
        rev_num = rev_num * 10 + last_digit
        num  = num //10
    return orig_num == rev_num
num = int(input("Please enter the number: "))
print(is_palindrome(num))
```
### ~ Count how many numbers from 1 to N are divisible by 3 or 5
```
def count_div_three_five(num):
    count = 0
    for i in range(1, num+1):
        if ( i% 3 == 0 or i % 5 == 0):
            count += 1
    return count
num = int(input("Please enter the number: "))
print(count_div_three_five(num))
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
def right_star_triangle(rows):
    for i in range(1, rows + 1):
        print('*' * i)
num = int(input("Please enter number of rows: "))
right_star_triangle(num)
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
def number_triangle(rows):
    total = 0
    for i in range(1, rows + 1):
        total = (total * 10) + i
        print(total)
num = int(input("Please enter number of rows: "))
number_triangle(num)
# this above fails for greater than 9
###
def number_triangle_nested(rows):
    for i in range(1, rows +1):
        for j in range(1, i+1):
            print(j, end='')
        print()
num = int(input("Please enter the number: "))
number_triangle_nested(num)
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
def inverted_star_triangle(rows):
    for i in range(rows, 0, -1):
        print('*' * i)
num = int(input("Please enter number of rows: "))
inverted_star_triangle(num)
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
def print_multiplication_table(num):
    for i in range(1,11):
        print('{} * {} = {}'.format(i, num, num * i))
num = int(input("Enter the number for the table: "))
print_multiplication_table(num)
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
def is_prime(num):
    if num <= 1:
        return "Not Prime"
    else:
        for i in range(2, int(num ** 0.5) + 1):
            if num % i == 0:
                return "Not Prime"
        return "Prime"
num = int(input("Enter a number to check if it's prime: "))

print(is_prime(num))
```
### ~ Find all prime numbers up to N
Input: N = 10 → Output: 2, 3, 5, 7
```
def primes_upto(upto_num):
    for num in range(2, upto_num + 1):
        if is_prime(num):
            print(num, end=' ')
def is_prime(num):
    if num <= 1:
        return False
    for i in range(2, int(num ** 0.5) + 1):
        if num % i == 0:
            return False
    return True

upto_num= int(input("Enter a number  to list all prime numbers up to it: "))
primes_upto(upto_num)
```
### ~ Print factorial of a number using a loop
Input: 5 → Output: 120
```
def factorial(num):
    fact = 1
    for i in range(1, num + 1):
        fact *= i
    return fact
num = int(input("Enter a number to find its factorial: "))
print(factorial(num))
```
### ~ Check if a number is an Armstrong number
*An n-digit number is Armstrong if:
    sum of each digit raised to the power n == the number itself
    e.g., 153 = 1³ + 5³ + 3³ = 153*
```
def is_armstrong(num):
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
    return total == original
num = int(input("Enter a number to check if Armstrong: "))
print(is_armstrong(num))
```
e.g. 153 = 1³ + 5³ + 3³ → Output: True  
OR
you can convert the entered number into string, and get the length of the digits
```
def is_armstrong(num):
    str_num = str(num)
    count = len(str_num)
    total = 0
    for digit in str_num:
        total += int(digit) ** count
    return total == num

num = int(input("Enter a number to check if Armstrong: "))
print(is_armstrong(num))
```
### ~ Find GCD of two numbers using loops (not math.gcd)
*GCD (Greatest Common Divisor) or HCF (Highest Common Factor) is the largest positive integer that divides two or more integers without leaving a remainder.*
```
def calc_gcd(a,b):
    # Step 1: Start from the smaller of the two
    min_num = min(a, b)
    # Step 2: Loop from min_num down to 1
    for i in range(min_num, 0, -1):
        if a % i == 0 and b % i == 0:
            return i
a = int(input("Enter first number: "))
b = int(input("Enter second number: "))
print(calc_gcd(a, b))
```
There is the Euclidean idea:  
GCD(a, b) = GCD(b, a % b)  
Keep doing this until b becomes 0  
At that point, a is the GCD  
Means, we can use the second part
```
def calc_gcd(a,b):
    while b != 0:
        temp = b
        b = a % b
        a = temp
    return a
a = int(input("Enter first number: "))
b = int(input("Enter second number: "))
print(calc_gcd(a,b))
```
### ~ Find sum and average of N numbers
```
def get_sum(n):
    total = 0
    for i in range(n):
        num = float(input(f"Enter number {i+1}: "))
        total += num
    return total

def calculate_average(total, n):
    return total / n if n != 0 else 0

n = int(input("Enter how many numbers: "))
total = get_sum(n)
print(total)
average = calculate_average(total, n)
print(average)
```
### ~ Check if a number is a perfect number
*A number is perfect if the sum of its divisors (excluding itself) equals the number*  
e.g. 28 → 1 + 2 + 4 + 7 + 14 = 28
```
def check_perfect_num(num):
    sum_divisors = 0
    i = 1
    while i < num:
        if num % i ==0:
            sum_divisors += i
        i += 1
    return sum_divisors == num  
num = int(input("Enter a number to check if it's perfect: "))
print(check_perfect_num(num))
```
### ~  FizzBuzz:

Take two divisors from the user that checks if the number between 1 to 30 is divisible:  
→ Print “Fizz” if divisible by first, “Buzz” if divisible by second, and “FizzBuzz” if divisible by both
```
def fizzbuzz(div1, div2):
    if 0 < div1 < 16 and 0 < div2 < 16:
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
        print("the divisors are greater than 15")

div1 = int(input("Enter the first divisor less than 15: "))
div2 = int(input("Enter the second divisor less than 15: "))
fizzbuzz(div1, div2)
```
### ~ Repeated Digit Sum Until Single Digit
Input: 5674 → Output: 5+6+7+4 → 22 → 2+2 =4
```
def sum_to_single_digit(num):
    sum = 0
    while num > 0 or sum > 9:
        if num == 0: # if num reduces to 0 but sum has more than 2 digit
            num = sum
            sum = 0
        sum += num % 10
        num //= 10
    return sum
n = int(input("Please enter the number: "))
print(sum_to_single_digit(n)) 
```
### ~ Convert Roman numeral into numbers
<details>
<summary></summary>

- Basic Values: I=1, V=5, X=10, L=50, C=100, D=500, M=1000.   
I- f a numeral is followed by one of equal or lesser value, add its value.
Example: VIII = 5 + 1 + 1 + 1 = 8.  
- If a smaller numeral precedes a larger numeral, subtract the smaller from the larger.
Example: IV = 5 - 1 = 4.  
- Only I, X, and C can be subtracted, and only from the next two higher numerals:  
  - I before V (5) and X (10)  
  - X before L (50) and C (100)  
  - C before D (500) and M (1000)  
  - V, L, and D are never subtracted. pairs like IL, IC, VX, etc., are invalid
- No numeral can be repeated more than three times in a row (e.g., III is valid; IIII is not).
</details>

```
def char_to_value(ch):
    if ch == 'I':
        return 1
    elif ch == 'V':
        return 5
    elif ch == 'X':
        return 10
    elif ch == 'L':
        return 50
    elif ch == 'C':
        return 100
    elif ch == 'D':
        return 500
    elif ch == 'M':
        return 1000
    else:
        return 0


def is_valid_subtraction(s1, s2):
    if s1 == 1 and (s2 == 5 or s2 == 10):
        return True
    elif s1 == 10 and (s2 == 50 or s2 == 100):
        return True
    elif s1 == 100 and (s2 == 500 or s2 == 1000):
        return True
    else:
        return False


def roman_to_decimal(roman):
    i = 0
    result = 0

    while i < len(roman):
        ch = roman[i]
        s1 = char_to_value(ch)

        if i + 1 < len(roman):
            ch_next = roman[i + 1]
            s2 = char_to_value(ch_next)

            if s1 < s2:
                if not is_valid_subtraction(s1, s2):
                    break
                result = result + (s2 - s1)
                i = i + 2
                continue
        result = result + s1
        i = i + 1
    return result

user_input = input("Please enter a Roman numeral: ")
print(roman_to_decimal(user_input))
```