
### print() — Output to the Screen

Displays information (text, numbers, variables) on the terminal. It is commonly used for showing results, debugging, and interacting with the user.

Syntax:
`print(value1, value2, ..., sep=' ', end='\n')`

Examples:
```
print("Hello, World!")                # prints a string
print(5 + 3)                          # prints result of an expression
name = "Alice"
print("Welcome,", name)              # prints with variables
```
Customizing Output:
```
print("A", "B", "C", sep="-")        # Output: A-B-C
print("Loading", end="...")          # Output: Loading...
```

### input() — Getting User Input

Waits for user input from the keyboard, always returns a string.

Syntax:
`variable = input("Prompt message: ")`

Examples:
```
name = input("What is your name? ")
print("Hello,", name)

age = input("Enter your age: ")
print("You are", age, "years old.")
```
```
age = input("Enter your age: ")
print(age + 1)    # This will cause a TypeError!, age is string
>> TypeError: can only concatenate str (not "int") to str
```
so you'll often need to convert it for numeric operations
```
age = int(input("Enter your age: "))
print("Next year, you will be", age + 1)
```
### Comments
 - Comments help explain code for ownself and others.
 - Comment is ignored by Python interpreter.  

Python supports two types of comments:
1. Single-line Comment
Starts with a # symbol  
Everything after # on that line is ignored by Python

```
# This is a single-line comment
x = 5  # This sets x to 5
```

2. Multi-line Comment (Docstring or Block-style)  
You can use triple quotes ''' ... ''' or """ ... 
```
"""  
Commonly used for documentation, not just comments

'''
This is a multi-line comment
that spans multiple lines.
'''
```
Or:
```
"""
This is another way
to write multi-line comments.
"""
```

Notes:  
 - Use comments to describe logic, especially complex parts.  
 - Avoid over-commenting obvious lines (x = 5 # Set x to 5 is unnecessary).  
 - Keep comments short and meaningful.