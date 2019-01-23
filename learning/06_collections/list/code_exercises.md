The following are some examples that shows how you can use just loop to perform operartions on each element or selected element. Some will show in place while others create new list wherever relevant. Becuase we have not yet learnt to write our own functions in Python(that are yet to learn), you will see, how we prompt(ask) user to enter the space or comma separated multiple values as inputs and convert it into a list by using list comprehension.

The first step is bascially taking the input which we are used to so far, and because inputs always are string, we use `.replace(","," ")` method to replace commas into space (so we have only spaces as separator) and use `.spilt()` method and convert it into list


#### ~ Sum of all elements in a list
```
user_input = input("please enter space or comma separated numbers: ")
nums = [int(x) for x in user_input.replace(',', " ").split()]
total = 0
for num in nums:
    total += num
print(total)
```
*May also use list in-built sum function as: `sum(nums)`*
#### ~ Find the maximum element
```
user_input = input("please enter space or comma separated numbers: ")
nums = [int(x) for x in user_input.replace(',', " ").split()]
max_val = nums[0]
for num in nums:
    if num > max_val:
        max_val = num
print(max_val)
```
*May also use list in-built max function as: `max(nums)`*
#### ~ Count even numbers
```
user_input = input("please enter space or comma separated numbers: ")
nums = [int(x) for x in user_input.replace(',', " ").split()]
count = 0
for num in nums:
    if num % 2 == 0:
        count += 1
print(count)
```
#### ~ Swap the first and last elements
```
user_input = input("please enter space or comma separated numbers: ")
nums = [x for x in user_input.replace(',', " ").split()]
temp = nums[0]
nums[0] = nums[-1]
nums[-1] = temp
print(nums)
```
Or in pythonic way
```
nums[0], nums[-1] = nums[-1], nums[0]
print(nums)
```
#### ~ Reverse a list
In-place reverse, basically, modifies the same list by swapping elements  
*Note: But adding and deleting is not advised as the length will vary leading to wrong indexing*
```
user_input = input("please enter comma separated numbers or strings: ")
nums = user_input.replace(',', " ").split()
for i in range(len(nums) // 2):
    temp = nums[i]
    nums[i] = nums[-1-i]
    nums[-1-i] = temp
print((nums))
```
Alternatively, you can create a new reversed list by appending elements from the right to the left side in the given list.
Create a new reversed list by appending elements from right to left
```
nums = [1, 2, 3, 4]
reversed_list = []
for i in range(len(nums)-1, -1, -1):
    reversed_list.append(nums[i])
print(reversed_list)
```
<details>
<summary>More ways: Using slicing and built-in .reverse() method</summary>
You may use slicing to create a new reversed copy of the list (concise and Pythonic)

```
reversed_list = nums[::-1]
print(reversed_list)
```
Or to reverse the list in place using slicing syntax:
```
nums[:] = nums[::-1]
print(nums)
```
Or simply use the built-in .reverse() method for in-place reversal:
```
nums = [1, 2, 3, 4]
nums.reverse()
print(nums)
```
</details>

#### ~ Remove duplicates (manually)
```
user_input = input("please enter space or comma separated numbers: ")
nums = [int(x) for x in user_input.replace(',', " ").split()]
unique = []
for num in nums:
    if num not in unique:
        unique.append(num)
print(unique)
```
#### ~ Check if a list is sorted
```
user_input = input("please enter space or comma separated numbers: ")
nums = [int(x) for x in user_input.replace(',', " ").split()]
is_sorted = True
for i in range(len(nums)-1):
    if nums[i] > nums[i+1]:
        is_sorted = False
        break
print(is_sorted)
```
or may use all() to check if every pair of the current and next element is following increasing order like:  
`all([nums[i] <= nums[i+1] for i in range(len(nums) - 1)])`

#### ~ Find the index of an element

```
user_input = input("please enter space or comma separated numbers: ")
nums = [int(x) for x in user_input.replace(',', " ").split()]
user_target = int(input("Please enter the target: "))
found = False
for i in range(len(nums)):
    if nums[i] == user_target:
        print("Index:", i)
        found = True
        break
if not found:
    print("Not found")
```
Since the else block in a for loop only executes if the loop completes without hitting a break, we can use it to handle the "not found" case.
This is more Pythonic and avoids using extra flag variables.
```
for i in range(len(nums)):
    if nums[i] == user_target:
        print("Index:", i)
        break
else:
    print("Item not found.")
``` 
*May also use list in-built `.index()` function as: `nums.index(target)` but raises ValueError*
#### ~ Print only positive numbers
```
user_input = input("please enter space or comma separated numbers: ")
nums = [int(x) for x in user_input.replace(',', " ").split()]
for num in nums:
    if num > 0:
        print(num)
```
#### ~ Count how many times a number appears
```
user_input = input("please enter space or comma separated numbers: ")
user_target = int(input("Please enter the target: "))
nums = [int(x) for x in user_input.replace(',', " ").split()]
count = 0
for num in nums:
    if num == user_target:
        count += 1
print(count)
*May also use list in-built `.count()` method of list as: `nums.count(target)` but raises ValueError*
```
#### ~ Insert an item at a specific index(shifting elements to the right)
```
user_input = input("please enter space or comma separated numbers: ")
nums = [x for x in user_input.replace(',', " ").split()]
insert = input("Please enter element to insert: ")
pos = int(input("Please enter position where to insert: "))

nums += [None]
for i in range(len(nums) -1,pos, -1):
    nums[i] = nums[i-1]
    
nums[pos] = insert
print(nums)
```
or use slicing
```
user_input = input("please enter space or comma separated numbers: ")
nums = [x for x in user_input.replace(',', " ").split()]
insert = input("Please enter element to insert: ")
pos = int(input("Please enter position where to insert: "))
new_nums = nums[:pos]+[insert]+nums[pos:]
print(new_nums)
```