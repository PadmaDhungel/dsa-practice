*Note: The logic here is rewritten using functions purely for practice.  
 In real code, wrapping built-ins like len() or upper()
isn't needed unless adding extra logic.
We're using them here to learn function structure.* 
### ~ Name Length
Ask the user for their name and print the total number of characters.
```
def name_length(name):
    return len(name)
name = input("Enter your name: ") # -> David Lu
print("Length of your name:", name_length(name)) # -> 8
```
### ~ First and Last Character
Take a word and print the first and last characters.
```
def first_and_last_char(word):
    first_char = word[0]
    last_char = word[-1]
    return first_char, last_char # comma separated are returned as tuple
word = input("Enter a word: ") # -> Orange
first_char,last_char = first_and_last_char(word)#tuple unpacking
print("First character:", first_char) # -> O
print("Last character:", last_char) # -> e
```
*empty string raises an IndexError*
### ~ Reverse the String
Take a string input and print it in reverse.
```
def reverse_string(text):
    return text[::-1]
text = input("Enter text: ") # -> Lily Lake
reversed_string = reverse_string(text)
print("Reversed:", reversed_string) # -> ekaL yliL
```
### ~ Convert to Uppercase and Lowercase
Convert input text to both uppercase and lowercase.
```
def upcase_and_lowcase(text):
    upper = text.upper()
    lower = text.lower()
    return upper, lower
text = input("Enter any text: ") # -> Mind Tree
upper_case, lower_case = upcase_and_lowcase(text)
print("Uppercase:", upper_case) # -> MIND TREE
print("Lowercase:", lower_case) # -> mind tree
```
### ~ Full Name Formatter
Ask for first and last names, and print them in title case.
```
def format_full_name(first, last):
    full_name = first + " " + last
    return full_name.title()
first = input("Enter your first name: ") # -> david
last = input("Enter your last name: ") # -> lu
format_name = format_full_name(first, last)
print("Formatted Name:", format_name) # -> Formatted Name: David Lu
```
### ~ Extract Domain from Email
Ask the user for an email and extract the domain.
```
def extract_domain(email):
    domain = email.split('@')[1]
    return domain
email = input("Enter your email: ") # -> davidlu@ymail.com
domain = extract_domain(email)
print("Email domain:", domain) # -> Email domain: ymail.com
```
*If the email does not contain '@', IndexError is raised* 

### ~ Extract Username from Email
Input: example@gmail.com → Output: example
```
def extract_username(email):
    username = email.split('@')[0]
    return username
email = input("Enter your email: ") # -> davidlu@ymail.com
username = extract_username(email)
print("Username:", username) # -> Username: davidlu
```
### ~ Find Position of a Substring
Ask for a sentence and a word to find in it, then print the index.
```
def find_position(sentence, word):
    position = sentence.find(word)#returns the first one
    return position
sentence = input("Enter a sentence: ") # -> This is a sentence.
word = input("Enter the word to find: ") # -> sent
position = find_position(sentence, word)
print("Position of the word:", position) # -> Position of the word: 10
```
*Returns -1 if the word isn't found*  
*This function may not return exact standalone position, if they are found ealier as part in words before than the standalone words. eg include 'be','me','a'* 
### ~ Replace Spaces with Underscores
Convert a sentence into snake_case. These are words connected by underscores replacing spaces.
```
def to_snake_case(text):
    snake_case = text.replace(" ", "_")
    return snake_case
text = input("Enter a sentence: ") # -> This is a sentence.
snake_case = to_snake_case(text)
print("snake_case:", snake_case) # -> snake_case: This_is_a_sentence.
```
### ~ Count Characters (Excluding Spaces)
Take a string and count characters excluding spaces.
```
def count_without_spaces(text):
    no_spaces = text.replace(" ", "")
    return len(no_spaces)
text = input("Enter some text: ") # -> This is a sentence.
no_spaces = count_without_spaces(text)
print("Character count (no spaces):", no_spaces) # -> Character count (no spaces): 16
```
### ~ Check for a Word in a Sentence
Ask for a word and a sentence. Check if the word is present.
```
def has_word(sentence, word):
    return word in sentence
sentence = input("Enter a sentence: ") # -> This is a sentence.
word = input("Enter a word: ") # -> sent
print("Is word present?", has_word(sentence, word)) # -> Is word present? True
```
*'in' is case sensitive, so different cases word may not match*  
 
*This function may return true if it finds the searched word within other string too, if they are found ealier as part in words before than the standalone words. eg include 'be','me','a'*
### ~ Convert "hello world" to "Hello World"
Ask for a phrase and convert it to title case.
```
def to_title_case(phrase):
    return phrase.title()
phrase = input("Enter a phrase: ") # -> hello world
print("Title case:", to_title_case(phrase)) # -> Title case: Hello World
```
### ~ Print Each Character with Space Between
Ask for a word and print its letters spaced out.
```
def spaced_text(text):
    spaced = " ".join(text)
    return spaced
text = input("Enter a word: ") # -> hello
spaced = spaced_text(text)
print("Characters with space:", spaced) # -> Characters with space: h e l l o
```
### ~ Trim Input String
Remove leading and trailing spaces from user input.
```
def trim_string(text):
    return text.strip()
text = input("Enter a string with spaces: ") # ->    hello world
print("Trimmed string:",trim_string(text)) # -> Trimmed string: hello world
```
### ~ Format Greeting with Name and Age
Ask the user for their name and age, and print a formatted greeting.
```
def format_greeting(name, age):
    greeting = "Hello, {}! You are {} years old.".format(name, age)
    return greeting
name = input("Enter your name: ") # -> Alice
age = input("Enter your age: ") # -> 23
print(format_greeting(name, age)) # -> Hello, Alice! You are 23 years old.
```
### ~ Escape Quotes in Output
Take input with quotes and show how to escape them.
```
def escape_quotes(text):
    escaped = text.replace('"', '\\"')
    return escaped
quote = input("Enter something with quotes: ") # -> She said "hello"
print("Escaped version:", escape_quotes(quote)) # -> Escaped version: She said \"hello\"
```
### ~ Swap Two Words
Ask for two words and swap their values.
```
def swap_words(a, b):
    a, b = b, a
    return a, b
a = input("Enter first word: ") # -> hello
b = input("Enter second word: ") # -> world
a, b = swap_words(a, b)
print("After swapping:")
print("First word:", a) # -> First word: world
print("Second word:", b) # -> Second word: hello
```
### ~ Check if Input is All Digits
Input a string and check if it contains only digits.
```
def is_all_digits(text):
    return text.isdigit()
text = input("Enter something: ") # -> 1234
print("Is numeric:",is_all_digits(text)) # -> Is numeric: True
``` 
*Strings containing only digits 0–9, if commas, points as floats are not checked*

### ~ Check for Alphabetic or Alphanumeric
Input a string and check whether it contains only letters (isalpha) or a mix of letters and digits (isalnum).
```
def is_alpha(text):
    return text.isalpha()
def is_alnum(text):
    return text.isalnum()
text = input("Enter something: ") # -> hello123
print("Is alphabetic?", is_alpha(text))   # False
print("Is alphanumeric?", is_alnum(text)) # True
```
### ~ Make it URL Friendly
Convert a string like "My Blog Post" to "my-blog-post".
```
def to_url_friendly(text):
    url_friendly = text.strip().lower().replace(" ", "-")
    return url_friendly
text = input("Enter a title: ") # -> My Blog Post
print("URL version:", to_url_friendly(text)) # -> URL version: my-blog-post
```
### ~ Display Text in a Box
Simple text framing using string repetition.
```
def display_in_box(text):
    border = "*" * (len(text) + 4)
    decor_text = "* {} *".format(text)
    return border,decor_text
text = input("Enter a word: ") # -> Hello
border,middle = display_in_box(text)
print(border)           # -> *********
print(middle)           # -> * Hello *
print(border)           # -> *********
```
### ~ Check Palindrome
A palindrome is a word that reads the same forward and backward.
```
def is_palindrome(text):
    normalized = text.lower().replace(" ", "")
    return normalized == normalized[::-1]
text = input("Enter a word: ") # -> radar
print("Is palindrome:", is_palindrome(text)) # -> True
```
*THe above is case-sensitive and space-sensitive. So "Radar" or "nurses run" would return False. so we need to use .lower().replace(" ", "") otherwise*