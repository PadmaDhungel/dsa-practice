## Loops (For and While)
Loops allow you to repeat a block of code multiple times. Python provides two main loop types:

 - for loop – when you know how many times to iterate
 - while loop – when you loop based on a condition that remains true

### for Loop
Used to iterate over a sequence (like a list, tuple, string, or range) and execute a block of code for each item.
```
for item in iterable:
    # code block
```
Examples
<details>
<summary>Iterating through a range</summary>

```
for i in range(3):
    print(i)
# Output: 
#    0
#    1
#    2
```
</details>

<details>
<summary>Iterating through a string</summary>

```
for char in "Python":
    print(char)
# Output:
# P
# y
# t
# h
# o
# n
```
</details>
<details>
<summary> Iterating through a list</summary>

```
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print("I like {}".format(fruit))
# Output:
# I like apple
# I like banana
# I like cherry
```
</details>


#### Commonly used iterables
 - range(n) – generates numbers from 0 to n-1
 - range(start, stop, step) - More flexible range with custom start, stop and step values
 - Lists, tuples, sets - Iterate through collection elements
 - dictionaries - can loop through keys(default), values, or items

#### Range Function Reference
| Use Case              | Code              |
|-----------------------|-------------------|
| 0 to 4                | `range(5)`        |
| 1 to 5                | `range(1, 6)`     |
| Even numbers 0 to 10  | `range(0, 11, 2)` |
| Reverse 5 to 1        | `range(5, 0, -1)` |

### Loop without using index
#### Repeat something 5 times; index not needed
```
for _ in range(5):
    print("Hello")
```
*Tip: Use _ as throwaway variable*

------ 
### While Loop
A while loop repeats a block of code as long as a specified condition evaluates to True.

```
while condition:
    # Code to execute while condition is True
```
Example (Basic loop)
```
x = 3
while x > 0:
    print(x)
    x -= 1
# Output:   
#    3
#    2
#    1
```
While loop with user input
```
while True:
    user_input = input("Type 'exit' to quit: ")
    if user_input == "exit":
        break
```
*Use while loops when the number of iterations is unknown or depends on user input or external conditions.*

#### Loop Control Statements
| Keyword    | Description                            |
| ---------- | -------------------------------------- |
| `break`    | Exits the loop immediately             |
| `continue` | Skips current iteration, goes to next  |
| `else`     | Runs if loop completes without `break` |

Examples
<details> 
<summary> break used in for:</summary>

```
for i in range(5):
    if i == 3:
        break
    print(i)
# Output: 
#    0
#    1
#    2
```
</details>
<details>
<summary>break used in while</summary>

```
while True:
    user_input = input("Type 'exit' to quit: ")
    if user_input == "exit":
        break
```
</details>
<details>
<summary>continue used in for</summary>

```
for i in range(5):
    if i == 3:
        continue
    print(i)
# Output: 
#    0
#    1
#    2
#    4
```
</details>
<details>
<summary>continue used in while</summary>

```
x = 0
while x < 5:
    x += 1
    if x % 2 == 0:
        # When x is even, continue skips the print() and moves to the next iteration.
        continue
    print(x)
# Output:
#    1
#    3
#    5
```
</details>
### Loop else Clause  

The else block after a for or while loop runs only if the loop finishes normally, without hitting a break statement.(i.e. without break) and has nothing to do with continue.
```
for num in range(2, 6):
    if num % 2 == 0:
        print("Even number found")
        break
else:
    print("No even numbers found")  # Won’t run if loop breaks
```
### Nested Loops
Loops inside other loops — useful for working with matrices or pattern problems.
<details>
<summary>for inside for - Grid Traversal</summary>

```
for i in range(3):
    for j in range(2):
        print("i={}, j={}".format(i,j))
# Output:
# i=0, j=0
# i=0, j=1
# i=1, j=0
# i=1, j=1
# i=2, j=0
# i=2, j=1
```
</details>
<details>
<summary>while inside while - Password Attempts</summary>

```
attempts = 0
max_attempts = 3

while attempts < max_attempts:
    password = input("Enter password: ")
    while password != "secret":
        print("Wrong password.")
        attempts += 1
        if attempts == max_attempts:
            print("Account locked.")
            break
        password = input("Try again: ")
    else:
        print("Login successful.")
        break
```
</details>
<details>
<summary>for inside while - Printing rows of stars</summary>
We want to print 3 rows of stars. Each row will have 5 stars.

```
row = 1

while row <= 3:             # Repeat 3 times (3 rows)
    for star in range(5):   # Print 5 stars in each row
        print("*", end="")  # Print star without moving to a new line
    print()                 # Move to next line after 5 stars
    row += 1

```
</details>
<details>
<summary>while inside for — Retry Each Task</summary>
For a list of tasks ["task1", "task2", "task3"], try each task until it succeeds on the second attempt. After each attempt, print which attempt it is and whether the task succeeded or needs to be tried again.

```
tasks = ["task1", "task2", "task3"]

for task in tasks:
    print("Processing", task)
    success = False
    attempts = 0

    while not success and attempts < 3:
        attempts += 1
        print("  Attempt #{}".format(attempts))
        if attempts == 2:
            print("  {} succeeded".format(task))
            success = True
        else:
            print("  Failed, retrying...")
```
</details>

## Best Practices
 
### General Guidelines
- Be cautious of **infinite loops** — always ensure the condition can become `False`.
Infinite loop
```
while True:
    print("Looping...")

```
This is good.
```
while True:
    break  # make sure to break
```
- Prefer **`for` over `while`** when iterating over a sequence.

```
# Good
for item in items:
    ...

# Avoid unless needed
i = 0
while i < len(items):
    ...
    i += 1
```

### Infinite Loop Pattern
```
while True:
    command = input(">>> ")
    if command == "quit":
        break
```
- Useful for CLI programs, game loops, menu systems, etc.

### Use pass if loop block is intentionally empty
for _ in range(5):
    pass  # Placeholder

#### Unpack directly in loops
```
pairs = [(1, 2), (3, 4)]
for x, y in pairs:
    print(x + y)
```
### Truthy/Falsy in Loop Conditions
| Value           | Considered As |
| --------------- | ------------- |
| `0`, `''`, `[]` | `False`       |
| Anything else   | `True`        |

```
while input("Continue? "):
    print("Looping again!")
```
### !!! Common Mistakes
| Mistake                                | Fix                                    |
| -------------------------------------- | -------------------------------------- |
| Forgetting to update `while` condition | Add changing variable or use `break`   |
| Using `for` when `while` is better     | Choose based on use case               |
| Not using `range()` in `for` loop      | Use `range(n)` when counting is needed |


### enumerate() - Loop with indexes
Enumerate is a powerful built-in tool that lets you to iterate  over a sequence and track the index at the same time.  
Syntax:
```
for index, item in enumerate(iterable, start=0):
    # use index and item
``` 
Example:
```
fruits = ["apple", "banana", "cherry"]

for index, fruit in enumerate(fruits):
    print(f"{index}: {fruit}")
# Output:
# 0: apple
# 1: banana
# 2: cherry
```
Starting from a custom index:
```
for index, fruit in enumerate(fruits, start=1):
    print(f"{index}. {fruit}")
# Output:
# 1. apple
# 2. banana
# 3. cherry
```
### zip() – Loop Over Multiple Sequences Together
zip() is used to loop over two or more iterables element-wise in parallel.

Syntax:
```
for item1, item2 in zip(iterable1, iterable2):
    # use item1 and item2
```
Example:
```
names = ["Alice", "Bob", "Charlie"]
scores = [85, 90, 95]
for name, score in zip(names, scores):
    print(f"{name} scored {score}")
# Output:
# Alice scored 85
# Bob scored 90
# Charlie scored 95
```
Unequal Lengths — Important!

If the iterables are unequal, zip() stops at the shortest one:
```
names = ["Alice", "Bob"]
scores = [85, 90, 95]
for name, score in zip(names, scores):
    print(f"{name} scored {score}")
# Output:
# Alice scored 85
# Bob scored 90
```
To include all items and fill in missing values, use zip_longest() from itertools:
```
names = ["Alice", "Bob"]
scores = [85, 90, 95]
from itertools import zip_longest
for name, score in zip_longest(names, scores, fillvalue="N/A"):
    print(f"{name} scored {score}")
# outputs
# Alice scored 85
# Bob scored 90
# N/A scored 95
```
Combining zip() and enumerate()  
You can even combine them to get both indexing and parallel iteration:
```
names = ["Alice", "Bob"]
scores = [85, 90]

for i, (name, score) in enumerate(zip(names, scores), start=1):
    print(f"{i}. {name} scored {score}")
# Output:
# 1. Alice scored 85
# 2. Bob scored 90
```