# Python: Variables and Data Types

## What is a Variable?

A **variable** is a container for storing data values. Variables allow programs to store, retrieve, and manipulate data.

Python is dynamically typed, meaning you don't have to declare the data type explicitly.

```python
x = 5
name = "John"
```
Variables can be reassigned to different types.
```
x = 42       # Integer
x = "hello"  # Now it's a string
```
## Variable Naming Rules

- Must begin with a letter (a–z, A–Z) or underscore (_)  
    <details>
    <summary><strong>Note:  Underscore Naming Patterns in Python (Click to Expand)</strong></summary>

    | Pattern      | Meaning / Use                                  |
    |--------------|-------------------------------------------------|
    | `_var`       | Internal or “protected” by convention           |
    | `__var`      | Name mangling (used in classes)                 |
    | `__var__`    | Dunder methods — special Python behavior        |
    | `_` (alone)  | Last result in REPL / throwaway variable        |

    </details>

- Can contain letters, numbers, underscores
- Case-sensitive (name, Name, NAME are different)  
*Examples:*  
  - Valid: `my_var`, `_score`,`age1`
  - Invalid: 1age, my-var, for (reserved word)

## Variable declaration methods
*Declaration (To declare the variable) means, to create a name in memory that refers to a value. And in python declaration is with value assignment (initialization in other languages).*
- Standard (single line)
    ```
    x = 10
    name = "Alice"
    ```
- Multiple Assignment (Same Line):  
`x, y, z = 1, 2, 3`
- or they can be different types too.  
`name, age, is_student = "Alice", 21, True`  
    But while doing so, the number of variables on the left must match the number of values on the right. Eg.
    - Valid: `a, b = 1, "hello"`
    - Invalid (ValueError): `x, y = 1, 2, 3` `ValueError: too many values to unpack (expected 2)`
- Same Value to Multiple Variables  
`a = b = c = 0`
- Unpacking from List, Tuples or string and assigning to variables  
    ```
    numbers = [1, 2, 3]
    x, y, z = numbers  ## x = 1, y = 2,z = 3
     ##or
    a, b, c = "ABC"
    ``` 
- Also we may use _ for the used values from collections(list, tuple);
  `x, _, z = (1, 2, 3)`  

## Python data types 

1. Numeric Types

    | Type      | Example        | Description              |Eg |
    | --------- | -------------- | ------------------------ | -- |
    | `int`     | `10`, `-5`     | Whole numbers            | `a = 10 ` |
    | `float`   | `3.14`, `-2.0` | Decimal numbers          |`b = 3.14 ` |
    | `complex` | `2+3j`         | Complex numbers (real+ img)|` c = 2 + 3j ` |

    *In complex number, the imaginary part is usually sufficed with 'i' in mathematics, but here it is 'j'.*  
2. String Types  
    `name = "Alice"` or  `greeting = 'Hello'`
    single quote (') or double quote (") - use same

3. Boolean Type (bool)  
    `is_happy = True` or `is_sad = False`
4. NoneType (None)  
    `result = None` to represent no value and declare but initialize later
5. Collection Types (Only preview — deeper later)  

| Type    | Example            | Description                   |
| ------- | ------------------ | ----------------------------- |
| `list`  | `[1, 2, 3]`        | Ordered, mutable collection   |
| `tuple` | `(1, 2, 3)`        | Ordered, immutable collection |
| `set`   | `{1, 2, 3}`        | Unordered, no duplicates      |
| `dict`  | `{"a": 1, "b": 2}` | Key-value pairs               |

#### Checking Data Types

Use the type() function to check a variable's type:
```
type(42)                 # <class 'int'>
type(56.76)              # <class 'float'>
type(5 + 2j)             # <class 'complex'>
type('e')                # <class 'str'>
type("tree")             # <class 'str'>
type(True)               # <class 'bool'>
type(None)               # <class 'NoneType'>
type([1, 2, 3])          # <class 'list'>
type((1, 2, 3))          # <class 'tuple'>
type({1, 2, 3})          # <class 'set'>
type({"a": 2, "b": 3})   # <class 'dict'>
```
#### False values (Evaluate to false)

| Value            | Description                        |
| ---------------- | ---------------------------------- |
| `None`           | Null value                         |
| `False`          | Boolean false                      |
| `0`, `0.0`, `0j` | Numeric zero (int, float, complex) |
| `''` / `""`      | Empty string                       |
| `[]`             | Empty list                         |
| `{}`             | Empty dictionary                   |
| `set()`          | Empty set                          |
| `tuple()`        | Empty tuple                        |
| `range(0)`       | Empty range                        |

*Other than the above, are true*
#### Type Conversion (Casting)

In Python, **type casting** is the process of converting one data type to another. There are two kinds of casting:

- Implicit Casting (Automatic) (a.k.a. type coercion):- Python **automatically converts** one data type to another during an operation **if it's safe** — this is called **implicit casting**.

    Python follows the implicit numeric type promotion chain `bool → int → float → complex`  
    True becomes 1 and False becomes 0 in int, and for float they become 1.0 and 0.0 and in complex 1+0j and 0+0j respectively during mathematical operation.

- Explicit Casting (Manual):- You can force Python to convert between data types using casting functions like int(), float(), str(), etc.

| Function       | Converts To    | Example                                         | Safe Conversion?                                         |
| -------------- | -------------- | ----------------------------------------------- | -------------------------------------------------------- |
| `int(x)`       | Integer        | `int("10")` → `10`                              |  Only if `x` is int-like (`"10"`, `3.5`) but not `int("abc")`                |
| `float(x)`     | Float          | `float("3.14")` → `3.14`                        |  Only if `x` is float-like (`"3.14"`, `5`) but not `float("abc") `           |
| `complex(x)`   | Complex number | `complex(5)` → `(5+0j)`                         | Generally safe for numbers and numeric strings         |
| `str(x)`       | String         | `str(123)` → `"123"`                            | Always safe                                            |
| `bool(x)`      | Boolean        | `bool([])` → `False`                            | Always safe                                            |
| `list(x)`      | List           | `list("abc")` → `['a','b','c']`                 | If `x` is iterable                                     |
| `tuple(x)`     | Tuple          | `tuple([1, 2])` → `(1, 2)`                      | If `x` is iterable                                     |
| `set(x)`       | Set            | `set([1, 2, 2])` → `{1, 2}`                     | If `x` is iterable with hashable items                 |
| `dict(x)`      | Dictionary     | `dict([('a', 1)])` → `{'a': 1}`                 |  Only if `x` is iterable of key-value pairs            |

To undertand the above terms like iterable, hashable, mutable & immutable
| Concept       | Means...                              | Examples                           |
| ------------- | ------------------------------------- | ---------------------------------- |
| **Iterable**  | Can be looped over (`for x in ...`)   | `list`, `str`, `dict`, `set`       |
| **Hashable**  | Can be used as `dict` keys / in `set` | `int`, `str`, `tuple`, `frozenset` |
| **Mutable**   | Can be changed after creation         | `list`, `dict`, `set`              |
| **Immutable** | Cannot be changed after creation      | `int`, `str`, `tuple`, `frozenset` |

