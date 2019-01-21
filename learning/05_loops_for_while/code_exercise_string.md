##  String-Based Problems
### ~ Count vowels and consonants in a string
```
input_str = input("Enter a string: ").lower()
vowels = "aeiou"
vowel_count = 0
consonant_count = 0
for ch in input_str:
    if ch.isalpha():  # only count letters
        if ch in vowels:
            vowel_count += 1
        else:
            consonant_count += 1

print("Vowels:", vowel_count)
print("Consonants:", consonant_count)
```
### ~ Reverse a string using loop (don’t use slicing)
```
input_str = input("Enter a string: ")
reversed_str = ""
for i in range(len(input_str) - 1, -1, -1):
    reversed_str += input_str[i]
print("Reversed string:", reversed_str)

```
### ~ Check if a string is a palindrome
A palindrome is a word, phrase, number, or sequence that reads the same forward and backward.
Input: "level" → Output: True
```
input_str = input("Please enter a test word: ")
n = len(input_str)
is_palindrome = True
for i in range(n//2):
    if input_str[i] != input_str[n-1-i]:
        is_palindrome = False
        break
print("Yes" if is_palindrome else "No") 
```
- Two pointer method
    <details>
    <summary>More on two pointer method</summary>
    The two-pointer method uses two variables moving from opposite ends of a string or array toward the center. It efficiently compares elements pairwise in a single pass, often used to check palindromes or find pairs, with O(n) time and no extra space. This technique is faster and cleaner than nested loops and applies to many algorithm problems.</details>

```
input_str = input("Please enter a test word: ")
left = 0
right = len(input_str)-1#len -> last_index+1
is_palindrome = True
while left < right:
    if input_str[left] != input_str[right]:
        is_palindrome = False
        break
    else:
        left += 1
        right -= 1
print("Yes" if is_palindrome else "No")  
```
#### ~ Write a program that takes an text input from user and returns the first non-repeating character in it. If all characters repeat, return 'None'.
*The comparison should be case-sensitive, meaning 'a' and 'A' are considered different characters.*
> input: `s = "aabccbd"` output: `d` >> d does not repeat  
> input: `s = "xxyz"` output: `y` >> y is the first to not repeat
> input: `s = "aabbcc"` output: `None` >> y is the first to not repeat
```
text = input("Please enter a test word: ")
foundChar = None
for i in range(len(text)):
    found = False
    for j in range(len(text)):
        if i != j and text[i] == text[j]:
            found = True
            break
    if not found:
        foundChar = text[i]
        break 
print(foundChar)
```

```
text = input("Please enter a test word: ")
for i in range(len(text)):
    found = False
    for j in range(len(text)):
        if i != j and text[i] == text[j]:
            found = True
            break
    else:
        print(text[i])
        break
else:
    print("None")
```
#### ~ Write a program that takes two strings as input and determines whether the second string is a rotation of the first.
*A string s2 is a rotation of string s1 if it can be formed by moving some number of characters from the beginning of s1 to its end, without changing the order of characters.*
```
input_str1 = input("Please enter first test word: ")
input_str2 = input("Please enter second test word: ")
cond = False
n = len(input_str1)

for _ in range(n):
    if input_str1 == input_str2:
        cond = True
        break
    input_str1 = input_str1[-1] + input_str1[:-1]

print(cond)
```
#### ~ Write a program that takes three strings: `s – the main text`, `s1 – the substring to be replaced` and `s2 – the replacement string`. Replace all occurrences of s1 in s with s2, and print the modified string.(.replace() disallowed)
```
s = input("Please enter first main word: ")
s1 = input("Please enter the substring to be replaced: ")
s2 = input("the replacement string: ")

# print(s.replace(s1,s2)) #disallowed
result = ""
i = 0
while i < len(s):
    if s[i:i+len(s1)] == s1:
        result += s2
        i+=len(s1)
    else:
        result += s[i]
        i += 1
print(result)
```
*In strings like "aaaay", replacing "aaa" with "x" will match only the first non-overlapping occurrence, resulting in "xay" — the code does not print "axy".*
#### ~ Find the length of the longest substring without repeating characters
> Substring is a part of string containing 1 or more adjacent(together) character, without breaking original order or sequence.
```
user_str = input("Please enter first main word: ")
cur_max = "" 
the_max = ""
i = 0
while i < len(user_str):
    cur_char = user_str[i]
    found_pos = -1
    #loop over the cur_max, to check if cur_char exist in cur_max and return index
    for j in range(len(cur_max)):
        if cur_char == cur_max[j]:
            found_pos = j
            break
    if found_pos != -1: # there was repetion, we need to reset cur_max by extracting text after repeated character
        cur_max = cur_max[found_pos + 1:] + cur_char
    else: # no repetition
        cur_max +=cur_char
        
    if len(cur_max) > len(the_max):
        the_max = cur_max

    i+=1
print(the_max)
```
#### ~ Determine if two strings s and t are isomorphic
Two strings of equal length are isomorphic if the characters in s can be replaced to get t, with the following conditions:
- Each character in s must map to exactly one character in t.
- No two characters in s may map to the same character in t.
- The character mapping must be consistent throughout the strings.
```
# user_str1 = input("Please enter first word: ")
# user_str2 = input("please enter second word: ")

isomor = True
if len(user_str1) != len(user_str2):
    isomor = False
else:
    for i in range(len (user_str1)):
        for j in range(i+1, len(user_str1)):
            if user_str1[i] == user_str1[j] and user_str2[i] !=user_str2[j]:
                isomor = False
                break
            if user_str1[i] != user_str1[j] and user_str2[i] ==user_str2[j]:
                isomor = False
                break
print(isomor)
```