
## Python Functions

### What is a Function?

A *function* is a block of reusable code designed to perform a specific task. Instead of writing the same code repeatedly, you define a function once and call it whenever needed.

### Why Use Functions?

- Code Reusability: Write once, use many times.
- Modularity: Break your program into smaller, manageable parts.
- Readability: Makes code easier to read and maintain.
- Avoid repetition: Helps avoid duplicated code.

### Defining and Calling a Function

You define a function using the `def` keyword, followed by the function name and parentheses.

```
def greet():
    print("Hello, World!")

greet()  # Calling the function
```
### Function: Parameters and Arguments
Functions can take inputs called parameters. When calling the function, you pass arguments.
```
def greet(name):
    print("Hello, {}!".format(name))

greet("Alice")
greet("Bob")
```
### Default Parameters

You can assign default values to parameters so that the function can be called without arguments.

```
def greet(name="Guest"):
    print("Hello, {}!".format(name))

greet()         # Hello, Guest!
greet("Alice")  # Hello, Alice!
```

### Return Statement

Functions can return values using the `return` keyword.

```
def add(a, b):
    return a + b

result = add(5, 3)
print(result)  # 8
```
- Difference between `print()` and `return`:
    - `print()` outputs the result but returns `None`.
    - `return` sends a value back to the caller for further use.  
    A function without return statement returns None. 

### Variable-Length Arguments (`*args` and `**kwargs`)

- `*args` allows passing a variable number of positional arguments.
- `**kwargs` allows passing a variable number of keyword arguments.

```
def add_all(*args):
    return sum(args)

print(add_all(1, 2, 3, 4))  # 10

def print_info(**kwargs):
    for key, value in kwargs.items():
        print("{}: {}".format(key,value))

print_info(name="Alice", age=30)
```
### Variable Scope: Local vs Global

- Variables inside functions are local and can't be accessed outside.
- Global variables are declared outside functions and can be accessed inside unless shadowed.

```
x = 10  # global variable

def func():
    x = 5  # local variable
    print(x)

func()  # 5
print(x)  # 10

```

Use the `global` keyword to modify global variables inside functions.

### Writing Docstrings
A docstring describes what a function does. It goes right under the function header.
```
def add(a, b):
    """Return the sum of a and b."""
    return a + b
```
### The main() Function in Python
In many languages like C or Java, programs start from a main() function.  
In Python, there's no strict requirement for a main() function, but it's commonly used for better structure — especially in larger programs.

### Why Use main() in Python?

- Improves readability
- Separates code execution from function definitions
- Helps avoid accidental execution when importing the script elsewhere  
Example:
```
def funcA():
    print("function A")

def main():
    funcA()

if __name__ == "__main__":
    main()
```
- funcA() is a normal function that does something.
- main() acts as the entry point to your program — it calls funcA() (or any other logic).
#### What Does if __name__ == "__main__" Mean?
- Every Python file has a built-in variable called __name__.
- If the file is run directly, __name__ == "__main__" is True.
- If the file is imported as a module, the condition is False.

*This allows you to prevent code from running when a file is imported elsewhere.*