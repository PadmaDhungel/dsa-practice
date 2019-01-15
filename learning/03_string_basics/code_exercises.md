
### ~ Name Length
Ask the user for their name and print the total number of characters.
```
name = input("Enter your name: ") # -> David Lu
print("Length of your name:", len(name)) # -> 8
```
### ~ First and Last Character
Take a word and print the first and last characters.
```
word = input("Enter a word: ") # -> Orange
print("First character:", word[0]) # -> O
print("Last character:", word[-1]) # -> e
```
*empty string raises an IndexError*
### ~ Reverse the String
Take a string input and print it in reverse.
```
text = input("Enter text: ") # -> Lily Lake
print("Reversed:", text[::-1]) # -> ekaL yliL
```
### ~ Convert to Uppercase and Lowercase
Convert input text to both uppercase and lowercase.
```
text = input("Enter any text: ") # -> Mind Tree
print("Uppercase:", text.upper()) # -> MIND TREE
print("Lowercase:", text.lower()) # -> mind tree
```
### ~ Full Name Formatter
Ask for first and last names, and print them in title case.
```
first = input("Enter your first name: ") # -> david
last = input("Enter your last name: ") # -> lu
full_name = first + " " + last
print("Formatted Name:", full_name.title()) # -> Formatted Name: David Lu
```
### ~ Extract Domain from Email
Ask the user for an email and extract the domain.
```
email = input("Enter your email: ") # -> davidlu@ymail.com
domain = email.split('@')[1]
print("Email domain:", domain) # -> Email domain: ymail.com
```
*If the email does not contain '@', IndexError is raised* 

### ~ Extract Username from Email
Input: example@gmail.com → Output: example
```
email = input("Enter your email: ") # -> davidlu@ymail.com
username = email.split('@')[0]
print("Username:", username) # -> Username: davidlu
```
### ~ Find Position of a Substring
Ask for a sentence and a word to find in it, then print the index.
```
sentence = input("Enter a sentence: ") # -> This is a sentence.
word = input("Enter the word to find: ") # -> sent
print("Position of the word:", sentence.find(word)) # -> Position of the word: 10
```
*Returns -1 if the word isn't found* 
### ~ Replace Spaces with Underscores
Convert a sentence into snake_case.
```
text = input("Enter a sentence: ") # -> This is a sentence.
snake_case = text.replace(" ", "_")
print("snake_case:", snake_case) # -> snake_case: This_is_a_sentence.
```
### ~ Count Characters (Excluding Spaces)
Take a string and count characters excluding spaces.
```
text = input("Enter some text: ") # -> This is a sentence.
no_spaces = text.replace(" ", "")
print("Character count (no spaces):", len(no_spaces)) # -> Character count (no spaces): 16
```
### ~ Check for a Word in a Sentence
Ask for a word and a sentence. Check if the word is present.
```
sentence = input("Enter a sentence: ") # -> This is a sentence.
word = input("Enter a word: ") # -> sent
print("Is word present?", word in sentence) # -> Is word present? True
```
*'in' is case sensitive, so different cases word may not match* 
### ~ Convert "hello world" to "Hello World"
Ask for a phrase and convert it to title case.
```
phrase = input("Enter a phrase: ") # -> hello world
print("Title case:", phrase.title()) # -> Title case: Hello World
```
### ~ Print Each Character with Space Between
Ask for a word and print its letters spaced out.
```
text = input("Enter a word: ") # -> hello
spaced = " ".join(text)
print("Characters with space:", spaced) # -> Characters with space: h e l l o
```
### ~ Trim Input String
Remove leading and trailing spaces from user input.
```
text = input("Enter a string with spaces: ") # ->    hello world
print("Trimmed string:", text.strip()) # -> Trimmed string: hello world
```
### ~ Format Greeting with Name and Age
Ask the user for their name and age, and print a formatted greeting.
```
name = input("Enter your name: ") # -> Alice
age = input("Enter your age: ") # -> 23
print("Hello, {}! You are {} years old.".format(name, age)) # -> Hello, Alice! You are 23 years old.
```
### ~ Escape Quotes in Output
Take input with quotes and show how to escape them.
```
quote = input("Enter something with quotes: ") # -> She said "hello"
print("Escaped version:", quote.replace('"', '\\"')) # -> Escaped version: She said \"hello\"
```
### ~ Swap Two Words
Ask for two words and swap their values.
```
a = input("Enter first word: ") # -> hello
b = input("Enter second word: ") # -> world
a, b = b, a 
print("After swapping:")
print("First word:", a) # -> First word: world
print("Second word:", b) # -> Second word: hello
```
### ~ Check if Input is All Digits
Input a string and check if it contains only digits.
```
text = input("Enter something: ") # -> 1234
print("Is numeric:", text.isdigit()) # -> Is numeric: True
``` 
*Strings containing only digits 0–9, if commas, points as floats are not checked*

### ~ Check for Alphabetic or Alphanumeric
Input a string and check whether it contains only letters (isalpha) or a mix of letters and digits (isalnum).
```
text = input("Enter something: ") # -> hello123
print("Is alphabetic?", text.isalpha())   # False
print("Is alphanumeric?", text.isalnum()) # True
```
### ~ Make it URL Friendly
Convert a string like "My Blog Post" to "my-blog-post".
```
text = input("Enter a title: ") # -> My Blog Post
url_friendly = text.strip().lower().replace(" ", "-")
print("URL version:", url_friendly) # -> URL version: my-blog-post
```
### ~ Display Text in a Box
Simple text framing using string repetition.
```
text = input("Enter a word: ") # -> Hello
border = "*" * (len(text) + 4) 
print(border)           # -> *********
print("*", text, "*")   # -> * Hello *
print(border)           # -> *********
```
### ~ Check Palindrome
A palindrome is a word that reads the same forward and backward.
```
text = input("Enter a word: ") # -> radar
print("Is palindrome:", text == text[::-1]) # -> True
```
*THe above is case-sensitive and space-sensitive. So "Radar" or "nurses run" would return False. so we need to use .lower().replace(" ", "") otherwise*