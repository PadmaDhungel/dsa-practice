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
def is_empty(text):
    if text.strip() == "":
        return "empty string."
    else:
        return f"You entered: {text}"

text = input("Enter some text: ")
print(is_empty(text))
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
def cap_start(word):
    if word[0].isupper():
        return "capital start"
    else:
        return "No capital start"
word = input("Enter a word: ")
print(cap_start(word))
```
alternative : using ASCII (ord()):
65-A, 66-B,......90-Z
```
def cap_start(word):
    if 65 <= ord(word[0]) <= 90:
        return "capital start"
    else:
        return "no capital start"
word = input("Enter a word: ")
print(cap_start(word))
```
#### ~ Check if an Email Ends with .com
.endswith() - safe, readable and pythonic
```
def email_ends_com(email):
    if email.endswith(".com"):
        return "Valid: Ends with .com"
    else:
        return "Invalid: Must end with .com"
email = input("Enter your email: ")
print(email_ends_com(email))
```
alternative: using slicing for .com(-4 from the last)
```
def email_ends_com(email):
    if email[-4:] == ".com":
        return "has .com."
    else:
        return "Does not have .com."
email = input("Enter your email: ")
print(email_ends_com(email))
```
#### ~ Check if String Length is Greater Than 10
```
def len_grt_ten(text):
    if len(text) > 10:
        return "Long text"
    else:
        return "Short text"

text = input("Enter text: ")
print(len_grt_ten(text))
```
#### ~ Check if Password Has '@' Symbol
word.find('@') or @ in word
```
def has_rate(password):
    if "@" in password:
        return "Password contains @"
    else:
        return "Password must contain @"
password = input("Enter your password: ")
print(has_rate(password))
```
alternative: using find('@") and check for > -1 value
```
def has_rate(password):
    if password.find("@") != -1:
        return "Password contains @"
    else:
        return "Password must contain @"
password = input("Enter your password: ")
print(has_rate(password))
```
#### ~ Check for Leading or Trailing Spaces
```
def has_outer_spaces(text):
    if text != text.strip():
        return "yes extra spaces"
    else:
        return "No extra spaces"
text = input("Enter a sentence: ")
print(has_outer_spaces(text))
```
alternative: test for " ", but fails if space is newline or tab and also raises index error, if the string is empty.
```
def has_outer_spaces(text):
    if text[0] == " " or text[-1] == " ":
        return "yes extra spaces"
    else:
        return "No extra spaces"
```
safer alternative ( with length check)
```
def has_outer_spaces(text):
    if len(text) > 0 and (text[0].isspace() or text[-1].isspace()):
        return "Has leading or trailing whitespace"
    else:
        return "No leading or trailing whitespace"
```
#### ~ Check if Two Words are Same (Ignore Case)
```
def are_words_same(a, b):
    if a.lower() == b.lower():
        return "Words match (case-insensitive)"
    else:
        return "Words do not match"
a = input("Enter first word: ")
b = input("Enter second word: ")
print(are_words_same(a, b))
```
#### ~ Check if Name Contains a Digit (Invalid Name)
Check if the username follows common rules used in many registration forms — it must:
- Contain at least one digit
- Be made up of only letters and numbers
- Not include any symbols, spaces, or special characters
```
def has_num(name):
    if name.isalnum() and not name.isalpha() and not name.isdigit():
        return"valid name: contains digits & string"
    else:
        return"invalid name: must contain digit"
name = input("Enter your name: ")
print(has_num(name))
```
*isalnum() checks if the string contains only string and number*  

*Above solution is Not highly favored — the logic is tightly packed and less intuitive due to double negatives. It gives no clear feedback and prevents early rejection, meaning all conditions are evaluated every time.*

```
def has_num(name):
    if not name.isalnum():
        return "Invalid: contains characters other than  letters or numbers"
    elif name.isalpha() or name.isdigit():
        return "Invalid: must contain both letters and digits"
    else:
        return "Valid: contains letters and digits"
name = input("Enter your name: ")
print(has_num(name))
```
#### ~ Check for 'Forbidden' Word in Text
```
def has_forbidden(text):
    if "forbidden" in text.lower():
        return "Inappropriate content found"
    else:
        return "Clean sentence"

text = input("Enter a sentence: ")
print(has_forbidden(text))
```
#### ~ Take input and check if the first and last character are the same.
```
def same_first_last(text):
    text = text.strip()  # Remove leading/trailing spaces
    if len(text) == 0:
        return "Empty input is not allowed"
    if text[0] == text[-1]:
        return "Starts and ends with the same character"
    else:
        return "Different start and end characters"
text = input("Enter a string: ")
print(same_first_last(text))
```
#### ~ Check if a String Has Exactly One Word
no spaces
```
def is_single_word(text):
    text = text.strip()
    if len(text) == 0:
        return "Empty input is not allowed"
    if " " in text:
        return "More than one word"
    else:
        return "Exactly one word"
text = input("Enter a string: ")
print(is_single_word(text))
```
#### ~ Check if a String is a Valid Simple Password

Password is valid if:  
length is at least 8, contains '@' but contains no spaces
```
def is_valid_password(password):
    if len(password) >= 8 and '@' in password and ' ' not in password:
        return "Valid password"
    else:
        return "Invalid password"
password = input("Enter password: ")
print(is_valid_password(password))
```
*More favoured is the fail fast approach as it stops unnecessary checks and provides clear message or error*
```
def is_valid_password(password):
    if len(password) < 8:
        return "Invalid: Password must be at least 8 characters."
    elif ' ' in password:
        return "Invalid: Password must not contain spaces."
    elif '@' not in password:
        return "Invalid: Password must include '@' symbol."
    else:
        return "Valid password"
password = input("Enter password: ")
print(is_valid_password(password))
```
#### ~ Check if a String Ends with a Vowel
Check if the last character of the input string is a vowel (a, e, i, o, u), case insensitive.
```
def ends_with_vowel(text):
    if text[-1].lower() in "aeiou":
        return "Ends with a vowel"
    else:
        return "Does not end with a vowel"
text = input("Enter a string: ")
print(ends_with_vowel(text))
```
#### ~ Check If Email has atleast '@'and '.'
```
def email_at_dot(email):
    if "@" in email and "." in email:
        return "Email looks valid"
    else:
        return "Invalid email format"
email = input("Enter your email: ")
print(email_at_dot(email))
```
#### ~ Check If Email Format is Roughly Valid
A roughly valid email here will contain exactly one '@' and at least one '.' placed somewhere after it, with neither character at the start or end. There must be at least two characters between the '@' and the '.', and the email must not contain any spaces.

```
def is_roughly_email(email):
    if email.count('@') == 1:
        pos_at = email.find('@')
        if pos_at != 0 and pos_at != len(email) - 1:
            dot_after_at = email.find('.', pos_at + 2)
            if dot_after_at != -1 and ' ' not in email:
                return "Valid email format"
            else:
                return "Invalid: Dot missing after '@' or contains spaces"
        else:
            return "Invalid: @ is at the start or end"
    else:
        return "Invalid: Email must contain exactly one @"

email = input("Enter your email: ")
print(is_roughly_email(email))
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