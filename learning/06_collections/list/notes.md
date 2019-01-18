## What are Lists in Python?
A list is one of Python's most versatile and commonly used data structures.   
~It allows you to store multiple items regardless of data type in a single variable.  
~Lists are ordered (due to indexing) and mutable (allowing updates to their contents).  
*Think of a list as a flexible container that can hold elements of any data type — integers, strings, floats, booleans, or even other lists (nested lists).*
```
# This is how you create a list
my_first_list = [1, 2, 3, 4, 5]
```
## Creating Lists
### Empty Lists
```
# Creating an empty list
empty_list_A = []
empty_list_B = list()  # Using the list() constructor
```
### Lists with Items
- List with integers: `numbers = [1, 2, 3, 4, 5]`
- List with strings: `fruits = ["apple", "banana", "cherry"]`
- Mixed data types: `mixed = [1, "hello", 3.14, True]`
- can have list inside list - called nested list:
`nested_list = [[1, 2], [3, 4], [5, 6]]`
- can have collection types too:
```
my_list = [
    (1, 2),                        # A tuple
    [3, 4, 5],                     # A list
    {"name": "Alice", "age": 25},  # A dictionary
    10,                            # An integer
    "hello",                       # A string
]
```
### List from Other Sequences(iterales)
| Source Type        | Example Code     | Result    | Notes      |
|--------------------|------------------|-----------|------------|
| String             | `list("hello")`  | `['h', 'e', 'l', 'l', 'o']`  | Splits each character into a separate list element  |
| Range              | `list(range(5))` | `[0, 1, 2, 3, 4]` | Efficient for generating sequences of numbers    |
| Tuple              | `list((1, 2, 3))`| `[1, 2, 3]` | Preserves order; tuples are immutable, lists are not  |
| Set                | `list({1, 2, 3})`| `[1, 2, 3]` (unordered)  | Order is **not guaranteed** (sets are unordered)    |
| Dictionary (keys)  | `list({'a': 1, 'b': 2})`| `['a', 'b']` | Converts only the keys by default    |
| Dictionary (values)| `list({'a': 1, 'b': 2}.values())`| `[1, 2]`  | Values only; order preserved in Python 3.7+                   |
| Dictionary (items) | `list({'a': 1, 'b': 2}.items())`| `[('a', 1), ('b', 2)]`  | Useful when key-value pairs are needed                        |

## Accessing List Elements
### Indexing
Lists are zero-indexed, meaning the first element is at index 0.  
> for the list: `fruits = ["apple", "banana", "cherry", "date"]`

| Index Type        | Code         | Result    | Description                   |
|-------------------|----------------------|-----------|-------------------------------|
| Positive Index     | `fruits[0]`          | `"apple"` | First element (index 0)       |
|                   | `fruits[1]`          | `"banana"`| Second element (index 1)      |
| Negative Index     | `fruits[-1]`         | `"date"`  | Last element                  |
|                   | `fruits[-2]`         | `"cherry"`| Second-to-last element        |

### Common Mistakes with Indexing

```
fruits = ["apple", "banana", "cherry"]

#  IndexError: list index out of range
# fourth_fruit = fruits[3]  # There is no fourth element!

#  IndexError: list index out of range
# empty_list = []
# first_item = empty_list[0]  # Empty list has no elements!
```
Always check if your index is valid before accessing it, especially when working with user input or variables.
>*If there's no colon, it's indexing, which returns a single element (not a list), and can raise IndexError if the index is invalid.*  
>*If an expression includes a colon (:), it's slicing, which returns a new sequence (like a list or string) that contains zero or more elements. More below*
### Slicing
You can extract a portion of a list using slicing.  
num = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
| Slice Expression |  Equivalent     | Description     | Result                         |
|------------------|-----------------|-----------------|--------------------------------|
| `num[0:3]` |`num[0:3:1]` | First three elements| `[0, 1, 2]`                |
| `num[:3]`  |`num[0:3:1]`| First three elements (shorthand) | `[0, 1, 2]`  |
| `num[4:]`  |`num[4:len(num):1]`| From index 4 to end    | `[4, 5, 6, 7, 8, 9]` |
| `num[-3:]` |`num[-3:len(num):1]`| Last three elements    | `[7, 8, 9]`       |
| `num[:-2]` |`num[0:-2:1]`| Except last two elements   | `[0, 1, 2, 3, 4, 5, 6, 7]`|
| `num[::2]` |`num[0:len(num):2]`| Every second element    | `[0, 2, 4, 6, 8]`   |
| `num[::-1]`|`num[len(num)-1::-1]`| Reversed list| `[9, 8, 7, 6, 5, 4, 3, 2, 1, 0]`|

## Modifying Lists
### Changing Elements
```
fruits = ["apple", "banana", "cherry"]

# Change the second element
fruits[1] = "blueberry"  # Now fruits = ["apple", "blueberry", "cherry"]
```
### Adding Elements
For the list `fruits = ["apple", "banana", "cherry"]`
- Add an element to the end
```
fruits.append("date")  # ["apple", "banana", "cherry", "date"]
```
- Insert an element at a specific position, and shift all elements to right
```
fruits.insert(1, "avocado")  # ["apple", "avocado", "banana", "cherry", "date"]
```
- Concatenate lists (returns a new list)
```
combined = fruits + ["grape", "honeydew"]
```
- Extend the list with another list (updates the left one)   
 -- Using +=
    ```
    fruits += ["cherry", "date"]
    print(fruits)  # ['apple', 'banana', 'cherry', 'date']
    ```
  -- Using .extend()
  
    ``` 
    more_fruits = ["elderberry", "fig"]
    fruits.extend(more_fruits)
    print(fruits) # ["apple", "avocado", "banana", "cherry", "date", "elderberry", "fig"]
    ```

### Removing Elements
All the methods below remove element and update the list but only pop returns the removed item while the others return None  
`fruits = ["apple", "banana", "cherry", "date", "berry"]`
| **Operation**  | **Code Example**  | **Description**    | **Notes / Output**                                        |
| -------- | ------------------- | ----------------- | --------------- |
| Remove by value <br>     | `fruits.remove("cherry")` | Removes first occurrence of the value , returns None        | List updates, e.g. `["apple", "banana", "date", "berry"]` |
| Remove by index and get value  | `removed = fruits.pop(1)`  | Removes element at index and returns it       | `removed` = `"banana"`, list updates  |
| Remove last element   | `last = fruits.pop()`  | Removes and returns last element   | `last` = `"berry"`, list updates     |
| Delete by index or slice   | `del fruits[0]` | Deletes element at index, returns None | List updates, e.g. `["date"]`   |
| Clear all elements   | `fruits.clear()`             | Removes all elements, empty list, returns None   | List becomes `[]`     |


### Common Mistakes When Modifying Lists

```
fruits = ["apple", "banana", "cherry"]

#  ValueError: list.remove(x): x not in list
# fruits.remove("mango")  # "mango" is not in the list!

#  IndexError: pop index out of range
# fruits.pop(10)  # There's no element at index 10!

```
Always check if an element exists before removing it, and verify that an index is valid before accessing it.
## Nested Lists
Lists can contain other lists, creating multi-dimensional structures.

```
# 2D list (a list of lists)
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

# Accessing elements in a nested list
first_row = matrix[0]  # [1, 2, 3]
element = matrix[1][2]  # 6 (row 1, column 2)

# Modifying elements in a nested list
matrix[0][0] = 0  # Change the top-left element to 0
```
## Common List Methods and Functions

for the fruits list `fruits = ["apple", "banana", "cherry"]`
### Python Built-in List Functions — Detailed Overview

| Function | Description & Type Notes   | Example   | Result     |
|----------|---------------------|-------------------|--------|
| `len()`  | Returns the number of elements in a list. Works with any iterable; counts only top-level elements. | `len(["apple", "banana", "cherry"])`     | `3`   |
| `min()`  | Returns the smallest element. Supports int, float, bool (0/1), and strings (lexicographically). Mixed incompatible types cause `TypeError`. | `min([3, 1, 4, 1, 5])`                    | `1`                   |
| `max()`  | Returns the largest element. Same type rules as `min()`.                                                  | `max([3, 1, 4, 1, 5])`                    | `5`                   |
| `sum()`  | Returns the sum of numeric elements (int, float, bool). Does **not** support strings or mixed types (raises `TypeError`). | `sum([3, 1, 4, 1, 5])`                    | `14`                  |
| `any()`  | Returns `True` if **any** element is truthy, else `False`. Works with any iterable and checks truthiness. | `any([0, "", None, "ok"])`         | `True`                |
| `all()`  | Returns `True` only if **all** elements are truthy, else `False`. Works with any iterable and checks truthiness. | `all([True, 1, "hello"])`                  | `True`                |
