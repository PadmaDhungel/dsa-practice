#### Good Practice: Spot the Specific Case Early -Fail Fast or Pass First 
When writing conditions, put the most obvious or specific case first to make your logic clear and easy to maintain.
- Use Fail Fast when you need to catch errors or invalid inputs early, especially if there are multiple or complex failure checks.
Examples: empty string, missing password symbols, invalid email format.
- Use Pass First when the success condition is simple, clear, and easy to check, and you want to emphasize the positive case.
Examples: word starts with a capital letter, two words match (ignoring case), string ends with a vowel.  

*This applies whether you’re using multiple if / elif / else blocks or combining conditions with and / or.*

-----------------------------------  
#### ~ Check if a String is Empty
```
text = input("Enter some text: ")
if text.strip() == "":
    print("empty string.")
else:
    print("You entered:", text)
```
<details>
<summary>Caution!! >>></summary>
A common way to check for an empty string is using len(text) == 0 or text == "".
However, this fails when the user enters only spaces or tabs (e.g., " " or "\t"), which technically aren't empty — their length is greater than 0, and they're not equal to "".

To handle such cases, use .strip(), which removes all leading and trailing whitespace.
If the result is an empty string after stripping, the input was either empty or contained only spaces/tabs.
</details>

#### ~ Check if a Word Starts with a Capital Letter
```
word = input("Enter a word: ")
if word[0].isupper():
    print("capital start")
else:
    print("No capital start")
```
alternative : using ASCII (ord()):
65-A, 66-B,......90-Z
```
word = input("Enter a word: ")
if 65 <= ord(word[0]) <= 90:
    print("capital start")
else:
    print("no capital start")
```
#### ~ Check if an Email Ends with .com
.endswith() - safe, readable and pythonic
```
email = input("Enter your email: ")
if email.endswith(".com"):
    print("Valid: Ends with .com")
else:
    print("Invalid: Must end with .com")
```
alternative: using slicing for .com(-4 from the last)
```
word = input("Enter a word: ")
if word[-4:] == ".com" :
    print("has .com.")
else:
    print("Does not have .com.")
```
#### ~ Check if String Length is Greater Than 10
```
text = input("Enter text: ")
if len(text) > 10:
    print("Long text")
else:
    print("Short text")
```
#### ~ Check if Password Has '@' Symbol
word.find('@') or @ in word
```
password = input("Enter your password: ")
if "@" in password:
    print("Password contains @")
else:
    print("Password must contain @")
```
alternative: using find('@") and check for > -1 value
```
password = input("Enter your password: ")
if password.find("@") != -1:
    print("Password contains @")
else:
    print("Password must contain @")

```
#### ~ Check for Leading or Trailing Spaces
```
text = input("Enter a sentence: ")
if text != text.strip():
    print("yes extra spaces")
else:
    print("No extra spaces")
```
alternative: test for " ", but fails if space is newline or tab and also raises index error, if the string is empty.
```
if text[0] == " " or text[-1] == " ":
    print("Has leading or trailing spaces")
else:
    print("No leading or trailing spaces")
```
safer alternative ( with length check)
```
if len(text) > 0 and (text[0].isspace() or text[-1].isspace()):
    print("Has leading or trailing whitespace")
else:
    print("No leading or trailing whitespace")
```
#### ~ Check if Two Words are Same (Ignore Case)
```
a = input("Enter first word: ")
b = input("Enter second word: ")
if a.lower() == b.lower():
    print("Words match (case-insensitive)")
else:
    print("Words do not match")
```
#### ~ Check if Name Contains a Digit (Invalid Name)
Check if the username follows common rules used in many registration forms — it must:
- Contain at least one digit
- Be made up of only letters and numbers
- Not include any symbols, spaces, or special characters
```
name = input("Enter your name: ")
if name.isalnum() and not name.isalpha() and not name.isdigit():
    print("valid name: contains digits")
else:
    print("invalid name: must contain digit")
```
*isalnum() checks if the string contains only string and number*  

*Not highly favored — the logic is tightly packed and less intuitive due to double negatives. It gives no clear feedback and prevents early rejection, meaning all conditions are evaluated every time.*

```
name = input("Enter your name: ")
if not name.isalnum():
    print("Invalid: contains characters other than  letters or numbers")
elif name.isalpha() or name.isdigit():
    print("Invalid: must contain both letters and digits")
else:
    print("Valid: contains letters and digits")
```
<details>
<summary>Disallowed method: used generator and for loop</summary>

```
name = input("Enter your name: ")
if any(char.isdigit() for char in name):
    print("Invalid name: contains digits")
else:
    print("Name looks good")
```
</details>

#### ~ Check for 'Forbidden' Word in Text
```
text = input("Enter a sentence: ")
if "Forbidden" in text.lower():
    print("Inappropriate content found")
else:
    print("Clean sentence")
```
#### ~ Take input and check if the first and last character are the same.
```
text = input("Enter a string: ")
if text[0] == text[-1]:
    print("Starts and ends with the same character")
else:
    print("Different start and end characters")
```
#### ~ Check if a String Has Exactly One Word
no spaces
```
text = input("Enter a string: ")
if " " in text:
    print("More than one word")
else:
    print("Exactly one word")
```
#### ~ Check if a String is a Valid Simple Password

Password is valid if:  
length is at least 8, contains '@' but contains no spaces
```
password = input("Enter password: ")
if len(password) >= 8 and '@' in password and ' ' not in password:
    print("Valid password")
else:
    print("Invalid password")
```
#### ~ Check if a String Ends with a Vowel
Check if the last character of the input string is a vowel (a, e, i, o, u), case insensitive.
```
text = input("Enter a string: ")
if text[-1].lower() in "aeiou":
    print("Ends with a vowel")
else:
    print("Does not end with a vowel")
```
#### ~ Check If Email has atleast '@'and '.'
```
email = input("Enter your email: ")
if "@" in email and "." in email:
    print("Email looks valid")
else:
    print("Invalid email format")
```
#### ~ Check If Email Format is Roughly Valid
A roughly valid email here will contain exactly one '@' and at least one '.' placed somewhere after it, with neither character at the start or end. There must be at least two characters between the '@' and the '.', and the email must not contain any spaces.

```
email = input("Enter your email: ")

if email.count('@') == 1:
    pos_at = email.find('@')
    
    if pos_at != 0 and pos_at != len(email) - 1:
        dot_after_at = email.find('.', pos_at + 2)  # dot must come at least 2 positions after '@'
        
        if dot_after_at != -1 and ' ' not in email:
            print("Valid email format")
        else:
            print("Invalid: Dot missing after '@' or contains spaces")
    else:
        print("Invalid: @ is at the start or end")
else:
    print("Invalid: Email must contain exactly one @")
```
## String Handling – Quick Cautions & Best Practices

### Safety First
-Check length before indexing (text[0], text[-1]) → Use: if len(text) > 0 and text[0] == ...
- Use .strip() to treat spaces or tabs as empty→ Use: if text.strip() == ""
- Don't slice blindly (text[-4:], etc.) → Use .endswith() when possible
### Input Normalization
- Use .lower() for case-insensitive checks
- Use .strip() to remove extra spaces before comparing→ a.strip().lower() == b.strip().lower()
### String Method Awareness
- .find() returns -1 if not found→ Correct: if text.find("@") != -1
- Use safe built-ins:.isupper(), .isdigit(), .isspace().startswith(), .endswith().count(), .split()
### Format & Content Checks
- "@" in email and "." in email" is not enough→ Validate positions, spacing, duplicates, no leading/trailing @ or .
- Combine conditions carefully→ if len(text) > 0 and text[-1].lower() in "aeiou"
- Use any(char.isdigit() for char in name) to detect digits