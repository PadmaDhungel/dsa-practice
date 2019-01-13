
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