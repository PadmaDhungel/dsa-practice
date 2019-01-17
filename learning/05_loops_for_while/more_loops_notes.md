
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