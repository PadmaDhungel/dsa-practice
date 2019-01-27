The following are some examples that shows how you can use just loop to perform operations on each element or selected element. Some will show in place while others create new list wherever relevant.  
As now we have learnt to write our own functions in Python, you will see, how we prompt(ask) user to enter the space or comma separated multiple values as inputs and convert it into a list by using list comprehension.  
The first step is basically taking the input which we are used to so far, and because inputs always are string, we use `.replace(","," ")` method to replace commas into space (so we have only spaces as separator) and use `.split()` method and convert it into list


#### ~ Sum of all elements in a list
```
def get_input_list():
    user_input = input("please enter space or comma separated numbers: ")
    nums = [int(x) for x in user_input.replace(',', " ").split()]
    return nums
def get_sum_list(arr):
    total = 0
    for num in arr:
        total += num
    return total
def main():
    arr = get_input_list()
    print(get_sum_list(arr))
if __name__ == "__main__":
    main()
```
*Alternate (Built-in): use `sum(nums)` instead*
#### ~ Find the maximum element
```
def get_input_list():
    user_input = input("please enter space or comma separated numbers: ")
    nums = [int(x) for x in user_input.replace(',', " ").split()]
    return nums
def get_max_list(arr):
    max_val = arr[0]
    for num in arr:
        if num > max_val:
            max_val = num
    return max_val
def main():
    arr = get_input_list()
    print(get_max_list(arr))
if __name__ == "__main__":
    main()
```
*Alternate (Built-in): use `max(nums)` instead*
#### ~ Count even numbers
```
def get_input_list():
    user_input = input("please enter space or comma separated numbers: ")
    nums = [int(x) for x in user_input.replace(',', " ").split()]
    return nums
def count_even_list(arr):
    count = 0
    for num in arr:
        if num % 2 == 0:
            count += 1
    return count
def main():
    arr = get_input_list()
    print(count_even_list(arr))
if __name__ == "__main__":
    main()
```
#### ~ Swap the first and last elements
```
def get_input_list():
    user_input = input("please enter space or comma separated numbers: ")
    nums = [x for x in user_input.replace(',', " ").split()]
    return nums
def swap_first_last(arr):
    temp = arr[0]
    arr[0] = arr[-1]
    arr[-1] = temp
    return arr
def main():
    arr = get_input_list()
    print(swap_first_last(arr))
if __name__ == "__main__":
    main()
```
Or in pythonic way
```
def swap_first_last(arr):
    arr[0], arr[-1] = arr[-1], arr[0]
    return arr
```
#### ~ Reverse a list
In-place reverse, basically, modifies the same list by swapping elements  
*Note: But adding and deleting is not advised as the length will vary leading to wrong indexing*
```
def get_input_list():
    user_input = input("please enter space or comma separated numbers: ")
    nums = [int(x) for x in user_input.replace(',', " ").split()]
    return nums
def do_reverse(arr):
    for i in range(len(arr) // 2):
        temp = arr[i]
        arr[i] = arr[-1-i]
        arr[-1-i] = temp
    return arr
def main():
    arr = get_input_list() 
    print(do_reverse(arr))
if __name__ == "__main__":
    main()
```
Alternatively, you can create a new reversed list by appending elements from the right to the left side in the given list.
Create a new reversed list by appending elements from right to left
```
def do_reverse(arr):
    reversed_list = []
    for i in range(len(arr)-1, -1, -1):
        reversed_list.append(arr[i])
    return reversed_list
```
<details>
<summary>More ways: Using slicing and built-in .reverse() method</summary>
You may use slicing to create a new reversed copy of the list (concise and Pythonic)

```
def do_reverse(arr):
    reversed_list = arr[::-1]
    return reversed_list
```
Or to reverse the list in place using slicing syntax:
```
def do_reverse(arr):
    arr[:] = arr[::-1]
    return arr
```
Or simply use the built-in .reverse() method for in-place reversal:
```
def do_reverse(arr):
    arr.reverse()
    return arr
```
</details>

#### ~ Remove duplicates (manually)
```
def get_input_list():
    user_input = input("please enter space or comma separated numbers: ")
    nums = [int(x) for x in user_input.replace(',', " ").split()]
    return nums
def get_duplicates(arr):
    unique = []
    printed = []
    for item in arr:
        if item not in unique:
            unique.append(item)
        else: 
            if item not in printed:
                print(item, end=" ")
                printed.append(item)
    if not printed:
        print(None)
def main():
    arr = get_input_list() 
    get_duplicates(arr)
if __name__ == "__main__":
    main()
```
#### ~ Check if a list(numeric) is sorted
```
def get_input_list():
    user_input = input("please enter space or comma separated numbers: ")
    nums = [int(x) for x in user_input.replace(',', " ").split()]
    return nums
def is_list_sorted(nums):
    for i in range(len(nums)-1):
        if nums[i] > nums[i+1]:
            return False
    return True
def main():
    arr = get_input_list() 
    print(is_list_sorted(arr))
if __name__ == "__main__":
    main()
```
or may use all() to check if every pair of the current and next element is following increasing order like:  
`all([nums[i] <= nums[i+1] for i in range(len(nums) - 1)])`

#### ~ Find the index of an element

```
def get_input_list():
    user_input = input("please enter space or comma separated numbers: ")
    nums = [int(x) for x in user_input.replace(',', " ").split()]
    user_target = int(input("Please enter the target: "))
    return nums,user_target
def get_index(arr, target):
    for i in range(len(arr)):
        if arr[i] == target:
            return i
    return -1
def main():
    arr,target = get_input_list() 
    print(get_index(arr,target))
if __name__ == "__main__":
    main()
```
Since the else block in a for loop only executes if the loop completes without hitting a break, we can use it to handle the "not found" case.
This is more Pythonic and avoids using extra flag variables.
```
def get_index(arr, target):
    for i in range(len(arr)):
        if arr[i] == target:
            return i
    else:
        return -1
``` 
or when we need both the element and index of the list, use enumerate()
```
def get_index(arr, target):
    for i,value in enumerate(arr):
        if value == target:
            return i
    else:
        return -1
```
*Alternate (Built-in): use `.index()` instead but raises ValueError*
#### ~ Print only positive numbers
```
def get_input_list():
    user_input = input("please enter space or comma separated numbers: ")
    nums = [int(x) for x in user_input.replace(',', " ").split()]
    return nums
def get_positives(nums):
    for num in nums:
        if num > 0:
            print(num, end=" ")
def main():
    arr = get_input_list() 
    get_positives(arr)
if __name__ == "__main__":
    main()
```
#### ~ Count how many times a number appears
```
def get_input_list():
    user_input = input("please enter space or comma separated numbers: ")
    user_target = int(input("Please enter the target: "))
    nums = [int(x) for x in user_input.replace(',', " ").split()]
    return nums, user_target
def count_target(arr,target):
    count = 0
    for ele in arr:
        if ele == target:
            count += 1
    return count
def main():
    user_list, user_target = get_input_list() 
    print(count_target(user_list,user_target))
if __name__ == "__main__":
    main()
*Alternate (Built-in): use `.count()` instead but returns 0 if not found*
```
#### ~ Insert an item at a specific index(shifting elements to the right)
```
def get_input_list():
    user_input = input("please enter space or comma separated numbers: ")
    nums = [x for x in user_input.replace(',', " ").split()]
    insert = input("Please enter element to insert: ")
    pos = int(input("Please enter position where to insert: "))
    return nums, insert, pos
def insert_value(arr,val,pos):
    arr += [None]
    for i in range(len(arr) -1,pos, -1):
        arr[i] = arr[i-1]
    arr[pos] = val
    return arr
def main():
    arr, val, pos = get_input_list()
    print(insert_value(arr,val,pos))
if __name__ == "__main__":
    main()
```
or use slicing
```
def get_input_list():
    user_input = input("please enter space or comma separated numbers: ")
    nums = [x for x in user_input.replace(',', " ").split()]
    insert = input("Please enter element to insert: ")
    pos = int(input("Please enter position where to insert: "))
    return nums, insert, pos
def insert_value(arr,val,pos):
    new_nums = arr[:pos]+[val]+arr[pos:]
    return new_nums
def main():
    arr, val, pos = get_input_list()
    print(insert_value(arr,val,pos))
if __name__ == "__main__":
    main()
```