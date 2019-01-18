### CLI Menu
- "Write a Python program that repeatedly displays a menu to the user and performs one of the following tasks based on the user's choice:  
    1. Print all even numbers up to a given number N.
    2. Calculate and print the sum and average of N user-entered numbers.
    3. Check whether a given number is a perfect number.
    4. Exit the program. 

    The program should continue to display the menu after each operation until the user chooses to exit. Ensure to handle invalid inputs gracefully by prompting the user again."

```
while True:
    print("\nMenu:")
    print("1. Print all even numbers up to N")
    print("2. Find sum and average of N numbers")
    print("3. Check if a number is perfect")
    print("4. Exit")

    choice = input("Enter your choice (1-4): ")

    if choice == '1':
        N = int(input("Enter N: "))
        i = 2
        while i <= N:
            print(i, end=" ")
            i += 2
        print()

    elif choice == '2':
        n = int(input("Enter how many numbers: "))
        total = 0
        i = 0
        while i < n:
            num = float(input(f"Enter number {i+1}: "))
            total += num
            i += 1
        average = total / n if n != 0 else 0
        print("Sum:", total)
        print("Average:", average)

    elif choice == '3':
        num = int(input("Enter a number to check if it's perfect: "))
        sum_divisors = 0
        i = 1
        while i < num:
            if num % i == 0:
                sum_divisors += i
            i += 1
        if sum_divisors == num:
            print(f"{num} is a Perfect Number.")
        else:
            print(f"{num} is NOT a Perfect Number.")

    elif choice == '4':
        print("Exiting program. Goodbye!")
        break

    else:
        print("Invalid choice! Please select from 1 to 4.")
```
### Calculator
- "Write a Python program that repeatedly asks the user to input two numbers and an operator, performs the arithmetic operation, and displays the result. The program should continue until the user decides to stop.  
1. The operations supported should be addition (+), subtraction (-), multiplication (*), and division (/).
2. If the user enters invalid numbers or an invalid operator, the program should display an error message and prompt again.
3. The program should handle division by zero gracefully.
4. If the result is a whole number (e.g., 5.0), it should be displayed as an integer (e.g., 5)."
```
while True:
    num1 = input("Enter first number: ")
    num2 = input("Enter second number: ")
    op = input("Enter operation (+, -, *, /): ")
    
    if not (num1.replace('.', '', 1).isdigit() and num2.replace('.', '', 1).isdigit()):
        print("Invalid input. Please enter numbers.")
        continue
    
    num1 = float(num1)
    num2 = float(num2)
    
    if op == '+':
        result = num1 + num2
    elif op == '-':
        result = num1 - num2
    elif op == '*':
        result = num1 * num2
    elif op == '/':
        if num2 == 0:
            print("Cannot divide by zero.")
            continue
        result = num1 / num2
    else:
        print("Invalid operator.")
        continue
    
    # Check if result is whole number
    if result.is_integer():
        result = int(result)
    
    print(f"Result: {result}")
    
    cont = input("Do you want to perform another calculation? (y/n): ").lower()
    if cont != 'y':
        print("Goodbye!")
        break
```
### Guess the Number Game

Write a Python program to let the user guess a randomly generated number between 1 and 20.
Generate the number using random.randint(1, 20).
- Repeatedly prompt the user to guess.
- After each guess, print:  
    "Too low!" for guess less than the number.  
    "Too high!" for guess greater than the number.  
    "Congratulations!." if correct.  
Continue until the user guesses correctly.
```
import random

number = random.randint(1, 20)
print("Guess the number between 1 and 20!")

guess = 0
while guess != number:
    guess = int(input("Enter your guess: "))
    if guess < number:
        print("Too low!")
    elif guess > number:
        print("Too high!")
    else:
        print("Congratulations! You guessed it.")
```
Simple Rock-Paper-Scissors (1 Round)

User plays one round against computer.
```
import random

print("Rock, Paper, Scissors!")

user_choice = input("Enter rock, paper or scissors: ").lower()

rand_num = random.randint(1, 3)
if rand_num == 1:
    computer_choice = "rock"
elif rand_num == 2:
    computer_choice = "paper"
else:
    computer_choice = "scissors"

print("Computer chose:", computer_choice)

if user_choice == computer_choice:
    print("It's a tie!")
elif (user_choice == "rock" and computer_choice == "scissors") or \
     (user_choice == "scissors" and computer_choice == "paper") or \
     (user_choice == "paper" and computer_choice == "rock"):
    print("You win!")
else:
    print("You lose!")
```