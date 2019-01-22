## List Operations

### Finding Elements
All methods in finding elements below are case-sensitive.
```
fruits = ["apple", "banana", "cherry", "banana", "date"]

# Check if an element exists
if "banana" in fruits:
    print("Yes, banana is in the list!")

# Find the index of the first occurrence
banana_index = fruits.index("banana")  # banana_index = 1

# Count occurrences
banana_count = fruits.count("banana")  # banana_count = 2

# ValueError: 'mango' is not in list
# mango_index = fruits.index("mango")  # Error because "mango" is not in the list
```
### Sorting and Reversing
Two methods for sorting:

     - .sort() - method is specific to list  
     - sorted() - method is to all iterables including list.  
    .reverse() - method is for reversing list.  

`list.sort(key=None, reverse=False)`  - modifies original list in place, returns None  
`sorted(iterable, *, key=None, reverse=False)` - retuns a new sorted list  
`list.reverse()` - modifies original list in place, returns None
```
# Sorting a list
numbers = [3, 1, 4, 1, 5, 9, 2]
numbers.sort()  # numbers = [1, 1, 2, 3, 4, 5, 9]

# Sort in descending order
numbers.sort(reverse=True)  # numbers = [9, 5, 4, 3, 2, 1, 1]

# Sorting strings (alphabetical order)
fruits = ["banana", "apple", "cherry"]
fruits.sort()  # fruits = ["apple", "banana", "cherry"]

# Creating a new sorted list (original unchanged)
original = [3, 1, 4, 1, 5]
sorted_list = sorted(original)  # sorted_list = [1, 1, 3, 4, 5], original remains [3, 1, 4, 1, 5]

# Reversing a list (in-place)
fruits.reverse()  # fruits = ["cherry", "banana", "apple"]
```

### List Comprehensions

List comprehensions provide a concise way to create lists based on existing sequences.
| Syntax    | Example    | Remarks / Concept            |
| --------------- | ------------- | --------------------- |
| `[expression for item in list(iterable)]`    | `squares = [x**2 for x in range(5)]` → `[0, 1, 4, 9, 16]`   | Regular: applies the same logic to all items    |
| `[expression for item in list(iterable) if condition]` | `evens = [x for x in range(5) if x % 2 == 0]` → `[0, 2, 4]` | Filtering: includes only items meeting the condition   |
| `[a if condition else b for item in list(iterable)]`| → `[x if x % 2 == 0 else -x for x in range(5)]`<br>`[0, -1, 2, -3, 4]` | Selective: all items included, logic depends on condition  |

*No break, continue and error checking like try and except*
#### More variants (based on the Above)
You can do nesting loops to as long as readable.
- You can include multiple for clauses (like a nested loop):
    ```
    pairs = [(x, y) for x in range(3) for y in range(2)]
    # Output: [(0, 0), (0, 1), (1, 0), (1, 1), (2, 0), (2, 1)]
    ```
- You can use filtering in nested loops and conditions:  
    ```
    pairs = [(x, y) for x in range(3) for y in range(3) if x != y]
    # Output: [(0, 1), (0, 2), (1, 0), (1, 2), (2, 0), (2, 1)]
    ```
- You can flatten a Nested List from 2D to 1D:
    ```
    matrix = [[1, 2], [3, 4], [5, 6]]
    flat = [num for row in matrix for num in row]
    # Output: [1, 2, 3, 4, 5, 6]
    ``` 
- <details>
    <summary>You can apply function too in list comprehension.</summary>
    You can call any function inside a list comprehension, including regular functions or lambdas.

    ```python
    def square(x):
        return x * x
    squares = [square(x) for x in range(5)]
    print(squares)  # Output: [0, 1, 4, 9, 16]
    ```
    Or using a lambda function inline:
    ```python
    squares = [(lambda x: x * x)(x) for x in range(5)]
    print(squares)  # Output: [0, 1, 4, 9, 16]
    ```
    Or assigning the lambda to a variable and using it:
    ```python
    square = lambda x: x * x
    squares = [square(x) for x in range(5)]
    print(squares)  # Output: [0, 1, 4, 9, 16]
    ```
    </details>
## List Copying
Copying means creating a new object that has the same content but a different identity (memory location). So, changes to one object won't affect the other.  
<details>
<summary>Imp: Copying integers, floats  and other primitives..</summary>

When you assign one variable to another with a primitive value (like an integer or float),
```
a = 10
b = a
```
both variables initially reference the same immutable object in memory. 
```
print(a,id(a), b,id(b))
# 10 11758280 10 11758280 
```
Because primitives are immutable, changing one variable creates a new object with a new memory address. 
```
b = 20  # Reassign b to a new integer object
print("After changing b:")
print(a,id(a), b,id(b))
# Outputs
# 10 11758280 10 11758280
# After changing a:
# 20 11758600 10 11758280
```

This makes it appear like a copy: modifying one variable doesn’t affect the other, even though they originally shared the same reference.
</details>
As you know, lists are mutable, so when you assign one list variable to another, both variables reference the same list object in memory.

```
list1 = [1, 2, 3]
list2 = list1
print(list1, id(list1), list2, id(list2))
#outputs: [1, 2, 3] 128681406352192 [1, 2, 3] 128681406352192
```
Changes to the list through either variable will affect the shared list. 
```
list1 = [1, 2, 3]
list2 = list1
print(list1, id(list1), list2, id(list2))
list2.append(4)
print("after appending 4 in list2")
print(list1, id(list1), list2, id(list2))
#Outputs:
# [1, 2, 3] 126671244331840 [1, 2, 3] 126671244331840
# after appending 4 in list2
# [1, 2, 3, 4] 126671244331840 [1, 2, 3, 4] 126671244331840
``` 
*Notice the [memory address(cpython)](https://docs.python.org/3.6/reference/datamodel.html) for both the list are same unlike primitive*  
So, simply assigning (like for primitive) does not work for list

org_list = [1, 2, 3]
| Method     | Example         | Considerations   | 
|------------|----------------|-----------------|
| `.copy()` <br> *~also for dict & set*  | `copy1 = org_list.copy()` | `copy1 = org_list.copy()`<br> `copy1[0] = 5`<br> `print(org_list) #>[1, 2, 3]` <br> `print(copy1) #>[5, 2, 3]`|
|`list()` constructor <br> *~all other iterables* | `copy2 = list(org_list)`|`copy2 = list(org_list)`<br> `copy2[1] = 5`<br> `print(org_list)  #>[1, 2, 3]` <br> `print(copy2) #>[1, 5, 3]` |
| **Using slicing** <br> *~syntactic sugar*| `copy3 = org_list[:]`| `copy3 = org_list[:]`<br> `copy3[2] = 5`<br> `print(org_list) #>[1, 2, 3]` <br> `print(copy3) #>[1, 2, 5]` |
| `copy.copy()` <br> *~needs import*        | `import copy` <br> `copy4 = copy.copy(org_list)` | `copy4 = copy.copy(org_list)`<br> `copy4[0] = 5`<br> `print(org_list) #> [1, 2, 3]` <br> `print(copy4) #> [5, 2, 3]` |

Shallow copies (from above methods) only duplicate the outer list. If your list contains nested mutable elements (like other lists) eg. `[[1, 2], 3, 4]`, those inner objects (inner list-[1,2]) are shared between the original and the copy. and you modify the inner list in either, both the original and the copy have their inner list changed.

 ```
 original = [[1, 2], 3, 4]
 sh_copy = original.copy() # or list(original) or copy.copy(original)
 sh_copy[0][0] = 5
 print("Original:{}".format(original)) # Output: [[5, 2], 3, 4]
 print("Shallow Copy:{}".format(sh_copy)) # Output: [[5, 2], 3, 4]
 ```
 Also,
```
original = [[1, 2], 3, 4]
sh_copy = original[:]
sh_copy[0][0] = 5
sh_copy[1] = 6
print("Original:{}".format(original))   # Output: [[5, 2], 3, 4]
print("Shallow Copy:{}".format(sh_copy))# Output: [[5, 2], 6, 4]
```
*Demonstrates not a true independent copy*
### Deep Copy for Nested Lists
To fully duplicate all levels of nested structures, use copy.deepcopy():
```
import copy
original = [[1, 2, 3],[4, 5], 6]

# Shallow copy (outer list only)
shallow = original[:]
shallow[0][0] = 10
print("Original:", original)   # [[10, 2, 3], [4, 5], 6]
print("Shallow:", shallow)     # [[10, 2, 3], [4, 5], 6]

# Deep copy (everything)
deep = copy.deepcopy(original)
deep[1][1] = 12
deep[0][2] = 11

print("Original:", original)   # [[10, 2, 3], [4, 5], 6]
print("Deep:", deep)           # [[10, 2, 11], [4, 12], 6]
```
## Common Pitfalls and Mistakes

### Modifying a List While Iterating

```
# WRONG: This will cause unpredictable behavior
numbers = [1, 2, 3, 4, 5]
for number in numbers:
    if number % 2 == 0:
        numbers.remove(number)  # Don't modify a list while iterating over it!

# CORRECT: Create a new list or use a list comprehension
numbers = [1, 2, 3, 4, 5]
odds = [num for num in numbers if num % 2 != 0]

```
### Understanding Mutability
```
# Lists are mutable (they can be changed after creation)
a = [1, 2, 3]
b = a  # Both variables reference the same list
b.append(4)  # Now a = [1, 2, 3, 4] as well!

```



## List Performance Considerations

Lists are efficient for certain operations, but not all:

- O(1) operations: Append, pop from end, indexing
- O(n) operations: Insert, remove, search, pop from beginning
- For frequent insertions/removals at the beginning, consider using collections.deque
- For large amounts of numerical data, consider using numpy arrays
