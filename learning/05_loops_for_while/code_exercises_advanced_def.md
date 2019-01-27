### CLI Menu
- "Write a Python program that repeatedly displays a menu to the user and performs one of the following tasks based on the user's choice:  
    1. Print all even numbers up to a given number N.
    2. Calculate and print the sum and average of N user-entered numbers.
    3. Check whether a given number is a perfect number.
    4. Exit the program. 

    The program should continue to display the menu after each operation until the user chooses to exit. Ensure to handle invalid inputs gracefully by prompting the user again."

```
def print_even(num):
    i = 2
    while i <= num:
        print(i, end=" ")
        i += 2
def sum_avg(count):
    total = 0
    i = 0
    while i < count:
        num = float(input(f"Enter number {i+1}: "))
        total += num
        i += 1
    average = total / count if count != 0 else 0
    print("Sum:", total)
    print("Average:", average)
def is_perfect(num):
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
def main():
    while True:
        print("\nMenu:")
        print("1. Print all even numbers up to N")
        print("2. Find sum and average of N numbers")
        print("3. Check if a number is perfect")
        print("4. Exit")

        choice = input("Enter your choice (1-4): ")
    
        if choice == '1':
            N = int(input("Enter N: "))
            print_even(N)
    
        elif choice == '2':
            n = int(input("Enter how many numbers: "))
            sum_avg(n)
    
        elif choice == '3':
            num = int(input("Enter a number to check if it's perfect: "))
            is_perfect(num)
    
        elif choice == '4':
            print("Exiting program. Goodbye!")
            break
    
        else:
            print("Invalid choice! Please select from 1 to 4.")
if __name__ == "__main__":
    main()
```
### Calculator
- "Write a Python program that repeatedly asks the user to input two numbers and an operator, performs the arithmetic operation, and displays the result. The program should continue until the user decides to stop.  
1. The operations supported should be addition (+), subtraction (-), multiplication (*), and division (/).
2. If the user enters invalid numbers or an invalid operator, the program should display an error message and prompt again.
3. The program should handle division by zero gracefully.
4. If the result is a whole number (e.g., 5.0), it should be displayed as an integer (e.g., 5)."
```
def operate(op, num1, num2):
    if op == '+':
        return num1 + num2
    elif op == '-':
        return num1 - num2
    elif op == '*':
        return num1 * num2
    elif op == '/':
        if num2 == 0:
            return "Cannot divide by zero."
        else:
            return num1 / num2
    return "Invalid operator."

def main():
    while True:
        num1 = input("Enter first number: ")
        num2 = input("Enter second number: ")
        op = input("Enter operation (+, -, *, /): ")
        
        if not (num1.replace('.', '', 1).isdigit() and num2.replace('.', '', 1).isdigit()):
            print("Invalid input. Please enter numbers.")
            continue
        
        num1 = float(num1)
        num2 = float(num2)
        
        result = operate(op, num1, num2)
        
        #Check if result is whole number
        if type(result) == float:
            if result.is_integer():
                print(f"Result: {int(result)}")
            else:
                print(f"Result: {result}")
        else:
            print(result)

        
        cont = input("Do you want to perform another calculation? (y/n): ").lower()
        if cont != 'y':
            print("Goodbye!")
            break
if __name__ == "__main__":
    main()
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
def guess_result(val, num):
    if val < num:
        return "Too low!"
    elif val > num:
        return "Too high!"
    else:
        return "Congratulations! You guessed it."

def main():
    number = random.randint(1, 20)
    print("Guess the number between 1 and 20!")
    guess = 0
    while guess != number:
        guess = int(input("Enter your guess: "))
        print(guess_result(guess,number))
        
if __name__ == "__main__":
    main()
```
### Simple Banking Simulator
Write a Python program that simulates simple banking actions:
- Start with a balance of 0.
- Repeatedly show a menu with options to:  
     Deposit money &nbsp; Withdraw money &nbsp; Check balance  &nbsp; Exit  
- For deposit/withdraw, prompt for amount and update balance accordingly.
- Show an error for invalid inputs or if withdrawal amount is more than balance.
- Keep running until the user chooses to exit.

```
def deposit(balance, amount):
    if amount > 0:
        balance += amount
        print(f"Deposited: {amount}")
    else:
        print("Invalid amount.")
    return balance

def withdraw(balance, amount):
    if 0 < amount <= balance:
        balance -= amount
        print(f"Withdrew: {amount}")
    else:
        print("Insufficient funds or invalid amount.")
    return balance

def get_user_choice():
    print("\n1. Deposit")
    print("2. Withdraw")
    print("3. Check Balance")
    print("4. Exit")
    return input("Enter your choice (1-4): ")

def main():
    balance = 0
    while True:
        choice = choice = get_user_choice()
        if choice == '1':
            amount = float(input("Enter amount to deposit: "))
            balance = deposit(balance, amount)
        elif choice == '2':
            amount = float(input("Enter amount to withdraw: "))
            balance = withdraw(balance, amount)
        elif choice == '3':
            print(f"Current balance: {balance}")
        elif choice == '4':
            print("Thanks for using the Banking Simulator!")
            break
        else:
            print("Invalid choice.")
        
if __name__ == "__main__":
    main()
```
### Simple Rock-Paper-Scissors (1 Round)
User plays one round against computer.
```
import random

def get_computer_choice():
    rand_num = random.randint(1, 3)
    if rand_num == 1:
        return "rock"
    elif rand_num == 2:
        return "paper"
    else:
        return "scissors"
def determine_winner(user, computer):
    if user == computer:
        return "It's a tie!"
    # \ are line breaks implying the current line continues next line
    elif ((user == "rock" and computer == "scissors") or 
         (user == "scissors" and computer == "paper") or 
         (user == "paper" and computer == "rock")):
        return "You win!"
    else:
        return "You lose!"
def main():
    print("Rock, Paper, Scissors!")
    user_choice = input("Enter rock, paper or scissors: ").lower()
    computer_choice = get_computer_choice()
    print("Computer chose:", computer_choice)
    result = determine_winner(user_choice, computer_choice)
    print(result)
if __name__ == "__main__":
    main()
```
### Two-Player Dice Game
Write a Python program to simulate a simple two-player dice game using only basic programming concepts: loops, conditionals, variables, and user input. Do not use functions (def) or advanced Python features.
<details>
<summary>Game rules</summary>

- The game is played between two players.  
- On a player's turn, they roll a six-sided die (values from 1 to 6).  
- If the player rolls a 1, their turn ends immediately and they earn 0 points for that turn.
- If they roll any other number (2–6), that number is added to their turn score.
- After each roll (except when it is 1), the player can choose to:  
    - Roll again, or
    - Hold, which ends their turn and adds the turn score to their total score.
- The game continues until one player reaches or exceeds 30 points, and that player is declared the winner.
</details>
<details>
<summary>Requirements</summary>

Your program must:
Use only:
- `while` loops  
- `if`, `else`, and `elif` statements  
- Variables  
- `print()` and `input()` functions  
- `random.randint()` from the `random` module  
Do not use:
- Lists, dictionaries, classes, or any other imports besides `random`  

Additional Requirements:
- Alternate turns between Player 1 and Player 2  
- Display the current score after each turn  
- Display a final message announcing the winner
</details>

```
import random

def player_turn(player_num):
    turn_score = 0
    print(f"Player {player_num}'s turn")
    while True:
        roll = random.randint(1, 6)
        print("You rolled a", roll)
        if roll == 1:
            print("Oops! You lose your turn.")
            return 0
        turn_score += roll
        print("Turn score:", turn_score)
        
        choice = input("Do you want to roll again? (y/n): ")
        if choice != "y":
            return turn_score
def main():
    player1_score = 0
    player2_score = 0
    score_to_win = 30  # You can change the target score
    current_player = 1
    print("Welcome to the Two-Player Dice Game!")
    print("First player to reach", score_to_win, "points wins!\n")
    while player1_score < score_to_win and player2_score < score_to_win:
        turn_score = player_turn(current_player)
        if current_player == 1:
            player1_score += turn_score
            print("Player 1 total score:", player1_score)
            current_player = 2
        else:
            player2_score += turn_score
            print("Player 2 total score:", player2_score)
            current_player = 1
        print("------------------------------")
    if player1_score >= score_to_win:
        print(" Player 1 wins with", player1_score, "points!")
    else:
        print(" Player 2 wins with", player2_score, "points!")
if __name__ == "__main__":
    main()
```