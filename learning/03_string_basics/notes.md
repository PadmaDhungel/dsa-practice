## String Basics in Python

Strings are sequences(immutable) of characters in Python. You can create strings using:
 - Single quotes: 'text'
 - Double quotes: "text"
 - Triple quotes for multiline: '''text''' or """text"""

```
text1 = 'Hello'
text2 = "World"
text3 = '''This is a
multiline string'''
```
#### Length of a string
len() returns the total number of characters in a string, including spaces and escape characters (like \n, \t), each counted as one character.
*Counting starts from 1, unlike string indexing which starts from 0.*
```
text1 = "Python"
text2 = "Basic Python"
text3 = "Test\nPython"
text4 = "Test/nPython"
print(len(text1)) #6   (Counts all characters starting from 1)
print(len(text2)) #12  (include the whitespace as a character)
print(len(text3)) #11  (\n is one character (newline))
print(len(text4)) #12  (just to show, / and n are treated as two separate characters)
```
#### Accessing Characters by index
 - Indexing starts from 0
 - Negative indexing starts from -1 (end of string)
```
word = "Python"
print(word[0])   # P
print(word[-1])  # n (last character)
```

#### Slicing strings
String slicing is a way to extract a portion (substring) of a string using the slice syntax:
`string[start:stop:step]`
Where:  
start → index where the slice starts (inclusive).  
stop → index where the slice ends (exclusive).  
step → interval between each character (default is 1).
```
text = "Hello, World"
print(text[0:5])   # Hello
print(text[:5])    # Hello
print(text[7:])    # World
print(text[::2])   # Hlo ol
print(text[1::2])  # el,Wrd
print(text[::-1])  # dlroW ,olleH (Reverse strings)
```
#### Case Manipulation

| Method           | Example                          | Description                                 |
|------------------|----------------------------------|---------------------------------------------|
| `lower()`        | `"HELLO".lower()` → `"hello"`    | Converts all characters to lowercase        |
| `upper()`        | `"hello".upper()` → `"HELLO"`    | Converts all characters to uppercase        |
| `capitalize()`   | `"hello".capitalize()` → `"Hello"` | Capitalizes first character only           |
| `title()`        | `"hello world".title()` → `"Hello World"` | Capitalizes first character of each word, apostrophes may not be handled well.                 |
| `swapcase()`     | `"Hello".swapcase()` → `"hELLO"` | Swaps case of all characters                |

---

### Checks & Tests

| Method           | Example                            | Description                                 |
|------------------|------------------------------------|---------------------------------------------|
| `isalpha()`      | `"abc".isalpha()` → `True`         | Returns True if all characters are alphabetic (A–Z/a–z)      |
| `isalnum()`      | `"abc123".isalnum()` → `True`      | Returns True if all characters are alphanumeric (A–Z, 0–9)  |
| `isdigit()`      | `"123".isdigit()` → `True`         | Returns True if all characters are digits (0–9)        |
| `isnumeric()`    | `"Ⅻ".isnumeric()` → `True`         | Checks if string is numeric (incl. Unicode) |
| `islower()`      | `"abc".islower()` → `True`         | Checks if all letters are lowercase         |
| `isupper()`      | `"ABC".isupper()` → `True`         | Returns True if all letters are uppercase         |
| `isspace()`      | `"   ".isspace()` → `True`         | Checks if all characters are whitespace     |

---

### Whitespace and Trimming

| Method           | Example                             | Description                                 |
|------------------|-------------------------------------|---------------------------------------------|
| `strip()`        | `"  hello  ".strip()` → `"hello"`   | Removes leading/trailing spaces             |
| `lstrip()`       | `"  hello".lstrip()` → `"hello"`    | Removes leading spaces                      |
| `rstrip()`       | `"hello  ".rstrip()` → `"hello"`    | Removes trailing spaces                     |

---

### Searching and Finding

| Method           | Example                              | Description                                 |
|------------------|--------------------------------------|---------------------------------------------|
| `find()`         | `"hello".find('l')` → `2`            | Finds first index of substring, or `-1`     |
| `rfind()`        | `"hello".rfind('l')` → `3`           | Finds last index of substring, or `-1`      |
| `index()`        | `"hello".index('l')` → `2`           | Like `find()`, but raises error if not found |
| `rindex()`       | `"hello".rindex('l')` → `3`          | Like `rfind()`, but raises error if not found |
| `startswith()`   | `"hello".startswith('he')` → `True`  | Checks if string starts with a substring    |
| `endswith()`     | `"hello".endswith('o')` → `True`     | Checks if string ends with a substring      |

---

### Replacing 
| Method           | Example                                | Description                                 |
|------------------|----------------------------------------|---------------------------------------------|
| `replace()`      | `"hello".replace("l", "x")` → `"hexxo"`| Replaces all occurrences of substring       |

---

### Joining and Splitting

| Method           | Example                                        | Description                                 |
|------------------|------------------------------------------------|---------------------------------------------|
| `split()`        | `"a,b,c".split(',')` → `['a', 'b', 'c']`       | Splits string using delimiter               |
| `splitlines()`   | `"hello\nworld".splitlines()` → `['hello', 'world']` | Splits on newline characters     |
| `join()`         | `" ".join(['a', 'b'])` → `"a b"`               | Joins list into string with separator       |

---
### String concatenation & Repetition
```
a = "Hello"
b = "World"
print(a + " " + b)      # Hello World
print(a * 3)            # HelloHelloHello
```
### Escape Characters within string
Sometimes, when you write text inside quotes, you want to use special characters like double quotes (") or backslashes (\). But if you use them directly, Python gets confused.

To fix this, you put a backslash (\) before these special characters. This tells Python, “Don’t treat this character as code, treat it like normal text.”
| Escape Code | What It Does                       | Example Code                  | Output           |
| ----------- | ---------------------------------- | ----------------------------- | ---------------- |
| `\"`        | Put a double quote inside a string | `print("He said \"Hello\".")` | He said "Hello". |
| `\'`        | Put a single quote inside a string | `print('It\'s OK.')`          | It's OK.         |
| `\\`        | Put a backslash inside a string    | `print("C:\\Users\\Name")`    | C:\Users\Name    |
| `\n`        | Start a new line                   | `print("Line1\nLine2")`       | Line1<br>Line2   |
| `\t`        | Add a tab space                    | `print("Tab\tSpace")`         | Tab    Space     |
### String Formatting
| Method            | Example                    | Description                            |
| ----------------- | -------------------------- | -------------------------------------- |
| `format()` method | `"Hello, {}".format(name)` | Older method for formatting strings    |
| `%` formatting    | `"Hello, %s" % name`       | Legacy formatting                      |
```
name = "Alice"
age = 30
print("Hello, {}".format(name))             # Hello, Alice
print("Hello, %s" % name)                   # Hello, Alice
```
### In Operator for Searching
The in keyword is a powerful way to search strings or substrings.
```
text = "Hello, world"
print("world" in text)      # True
print("bye" not in text)    # True
```
