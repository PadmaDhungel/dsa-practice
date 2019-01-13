## Concepts
### Comparison Operator
Used to compare values. These are the building blocks of conditions inside `if`, `elif`, and `else`.
<details>
<summary>More here(click me)</summary>

| Operator                | Expression | Result / Meaning                   |
| ----------------------- | ---------- | ---------------------------------- |
| `==` (equal to)         | `5 == 5`   | `True` if values are equal         |
| `!=` (not equal)        | `5 != 3`   | `True` if values are not equal     |
| `>` (greater than)      | `7 > 5`    | `True` if left is greater          |
| `<` (less than)         | `3 < 5`    | `True` if left is smaller          |
| `>=` (greater or equal) | `5 >= 5`   | `True` if left is greater or equal |
| `<=` (less or equal)    | `4 <= 6`   | `True` if left is smaller or equal |
</details>

Python converts conditions into True or False using the bool() function behind the scenes.

### Basic if-else Syntax:
>  **Common Mistakes**  
> - Using `=` instead of `==` in conditions  
> - Forgetting colons (`:`) after `if`, `else`, `elif`  
> - Incorrect indentation  
> - Using `else if` instead of `elif`
```
if condition:
    # code to execute if condition is True
else:
    # code to execute if condition is False
```
Example
```
age = 20
if age >= 18:
    print("Adult")
else:
    print("Minor")
#outputs: Adult
```
Nested if-else

Sometimes, you may want to check a condition inside another condition. This is known as nested if-else.
```
if condition1:
    if condition2:
        # code if both conditions are True
    else:
        # code if condition1 is True and condition2 is False
else:
    # code if condition1 is False
```
Example:
```
if is_logged_in:
    if is_admin:
        print("Welcome, Admin")
## Outputs: Welcome, Admin
```
### elif Statement:

> Use elif (not else if) in Python.
```
if condition1:
    # code if condition1 is True
elif condition2:
    # code if condition2 is True
else:
    # code if both conditions are False
```
Use elif instead of multiple ifs for better efficiency.
```
score = 70
if score >= 90:
    print("A")
elif score >= 60:
    print("B")
else:
    print("C")
## outputs : B
```
Nested if blocks can sometimes be replaced using logical operators (and, or) to simplify logic.
## Logical operator
| Operator | Description                                              | Example & Result             |
|----------|----------------------------------------------------------|-----------------------------|
| `and`    | Returns `True` if **both** operands are `True`, else `False` | `True and False` → `False`  |
| `or`     | Returns `False` if **both** operands are `False`, else `True` | `True or False` → `True`    |
| `not`    | Returns the **opposite** boolean value (negates)        | `not True` → `False`        |

```
x = 5
if x > 0 and x < 10:
    print("x is a positive single-digit number")
## Outputs: x is a positive single-digit number
```
#### Implementation of logical operator
```
if condition1 and condition2:
    # code if both are True
if condition1 or condition2:
    # code if at least one is True
if not condition1:
    # code if condition1 is False
```
### Ternary Conditional Operator

Python provides a shorthand for if-else in the form of the ternary operator. It’s a one-liner for simple conditional assignments.  
``` 
value_if_true if condition else value_if_false
```
```
age = 16
status = "Adult" if age >= 18 else "Minor"
print(status)
#Output: Minor
```
<details>
<summary> Example</summary>

```
age = 16
status = "Adult" if age >= 18 else "Minor"
print(status) # for age 16, outputs Minor
```
</details>

### Best practices
---------------

#### Boolean Truthy/Falsy
| Value                                  | Evaluates To |
| -------------------------------------- | ------------ |
| `0`, `''`, `[]`, `{}`, `None`, `False` | `False`      |
| Everything else                        | `True`       |

#### Short circuit Logic

Early returning circuits are more preferred
| Expression | Skips Evaluation If... |
| ---------- | ---------------------- |
| `a and b`  | `a` is `False`         |
| `a or b`   | `a` is `True`          |

#### Indentation Warning
Indentation is very essential and 4 spaces are preferred over tab in if-else blocks
``` 
if x > 5:
print("Too big")  #  IndentationError
## but this correct
if x > 5:
    print("Too big")
``` 
#### pass Statement
when you want an empty if or else. Show the pass keyword briefly.
``` 
if condition:
    pass  # do nothing for now
else:
    print("Something else")
``` 
Use pass as a placeholder when no action is needed. It keeps your code syntactically valid.

#### Avoid Nested ifs
``` 
# Don't do this
if is_logged_in:
    if is_admin:
        ...
# Instead do this
if is_logged_in and is_admin:
    ...
```

#### Prefer elif Over Multiple if

```
# 
if x == 1: ...
if x == 2: ...

# # Better: prevents unnecessary condition checks
if x == 1: ...
elif x == 2: ...

``` 
#### Use Booleans Directly
| Not Recommended         |  Pythonic        |
| ------------------------- | ----------------- |
| `if is_ready == True`     | `if is_ready`     |
| `if not is_empty == True` | `if not is_empty` |

#### Ternary for one liners
` status = "Pass" if score >= 50 else "Fail"` 

#### Use `not` wisely
```
if not is_valid: ...
# Avoid this:
if not (a > b and b > c):  #  harder to read due to double negatives
``` 