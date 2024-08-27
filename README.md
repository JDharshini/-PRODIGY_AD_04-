def print_board(board):
    """Prints the current state of the board."""
    print("\n" + " | ".join(board[0]) + "\n" + "---------\n" + " | ".join(board[1]) + "\n" + "---------\n" + " | ".join(board[2]) + "\n")

def check_winner(board, symbol):
    """Checks if the given symbol has won the game."""
    # Check rows
    for row in board:
        if all(s == symbol for s in row):
            return True
    
    # Check columns
    for col in range(3):
        if all(board[row][col] == symbol for row in range(3)):
            return True
    
    # Check diagonals
    if all(board[i][i] == symbol for i in range(3)):
        return True
    if all(board[i][2-i] == symbol for i in range(3)):
        return True
    
    return False

def check_draw(board):
    """Checks if the board is full and no winner exists."""
    return all(cell != ' ' for row in board for cell in row) and not (check_winner(board, 'X') or check_winner(board, 'O'))

def make_move(board, row, col, symbol):
    """Places the symbol on the board at the specified location if valid."""
    if board[row][col] == ' ':
        board[row][col] = symbol
        return True
    else:
        print("The cell is already occupied. Try again.")
        return False

def main():
    """Main function to run the Tic-Tac-Toe game."""
    while True:
        board = [[' ']*3 for _ in range(3)]
        current_player = 'X'
        winner = None

        while True:
            print_board(board)
            print(f"Player {current_player}'s turn")
            
            try:
                row = int(input("Enter the row (0, 1, or 2): "))
                col = int(input("Enter the column (0, 1, or 2): "))
                
                if 0 <= row <= 2 and 0 <= col <= 2:
                    if make_move(board, row, col, current_player):
                        if check_winner(board, current_player):
                            winner = current_player
                            break
                        elif check_draw(board):
                            break
                        current_player = 'O' if current_player == 'X' else 'X'
                else:
                    print("Invalid input. Please enter 0, 1, or 2 for row and column.")
            except ValueError:
                print("Invalid input. Please enter numerical values for row and column.")

        print_board(board)
        if winner:
            print(f"Player {winner} wins!")
        else:
            print("It's a draw!")

        play_again = input("Do you want to play again? (y/n): ").lower()
        if play_again != 'y':
            print("Thank you for playing! Goodbye!")
            break

if __name__ == "__main__":
    main()
Explanation:
print_board(board):

Prints the current state of the board in a readable format.
check_winner(board, symbol):

Checks if the specified symbol (X or O) has won the game by checking rows, columns, and diagonals.
check_draw(board):

Checks if the game has ended in a draw (board is full and no winner).
make_move(board, row, col, symbol):

Places the symbol on the board if the cell is empty. Prints a message if the cell is occupied.
main():

Contains the main game loop where players take turns to make moves.
Handles user input and checks for valid moves.
Determines the end of the game and prints the result.
Prompts the user to play again or exit.
Usage:
Run the Script: Save the code in a file named tic_tac_toe.py and run it using python tic_tac_toe.py.
Play the Game: Follow the prompts to make moves and see the game state. The game will continue until there is a winner or the board is full.
This implementation is a basic command-line Tic-Tac-Toe game. For a more advanced version, you might consider adding a graphical user interface (GUI) using a library like tkinter or enhancing the game with features like AI opponents.



You said:
give github readme for tic tac toe
ChatGPT said:
ChatGPT
Certainly! Here’s a sample README.md file for a Tic-Tac-Toe game implemented in Python. This README.md provides an overview of the project, instructions for setup and usage, and information about the project.

markdown

# Tic-Tac-Toe Game

Welcome to the **Tic-Tac-Toe Game**! 🎮 This is a simple command-line Tic-Tac-Toe game implemented in Python. It allows two players to take turns placing their symbols (`X` and `O`) on a 3x3 grid. The objective is to form a horizontal, vertical, or diagonal line of three symbols to win the game. The game also includes an option to reset and play again.

## Features

- 🎯 **Two-player mode**: Players alternate turns to place their symbols on the board.
- 🏆 **Win detection**: The game checks for a winner or a draw after every move.
- 🔄 **Reset and replay**: Players can choose to play another game or exit after a game concludes.

## Requirements

- Python 3.x 🐍

## Installation

1. **Clone the Repository**:

  
   git clone https://github.com/yourusername/tic-tac-toe.git
Navigate to the Project Directory:



cd tic-tac-toe
Usage
Run the Game:


python tic_tac_toe.py
Play the Game:

The game will prompt each player to enter the row and column (0, 1, or 2) where they want to place their symbol.
The game board will be displayed after each move.
The game will notify you of the winner or if the game ends in a draw.
After a game ends, you will have the option to play again or exit.
Example
markdown

Your To-Do List:
 | | 
---------
 | | 
---------
 | | 

Player X's turn
Enter the row (0, 1, or 2): 0
Enter the column (0, 1, or 2): 1

Your To-Do List:
 | X | 
---------
 | | 
---------
 | | 

Player O's turn
Enter the row (0, 1, or 2): 1
Enter the column (1, 2, or 3): 1

Your To-Do List:
 | X | 
---------
 | O | 
---------
 | | 

Player X wins!
Do you want to play again? (y/n): n
Thank you for playing! Goodbye!
Code Overview
tic_tac_toe.py: Contains the main code for the Tic-Tac-Toe game. Implements game logic, board display, move handling, and win detection.
License
This project is licensed under the MIT License. See the LICENSE file for details. 📝

Contributing
Feel free to fork the repository and submit pull requests. For bug reports or feature requests, please open an issue on GitHub. 🙌

Contact
For any questions or suggestions, you can reach out to your-email@example.com. 📧

Note: This is a basic implementation of Tic-Tac-Toe for educational purposes. For a more advanced version, consider adding a graphical user interface (GUI) or AI opponents. 🛠️




### How to Use This README

1. **Replace Placeholder Text**: Update the placeholder text (`https://github.com/yourusername/tic-tac-toe.git` and `your-email@example.com`) with your actual repository URL and contact information.
2. **Customize Further**: Adjust the content according to your needs and add any additional sections if necessary.

This `README.md` provides a clear and concise description of your Tic-Tac-Toe game, how to set it up, and how to use it.


You said:
give a readme github for Develop a Tic Tac Toe game app where two players can take turns to place their symbols (X or O) on a 3x3 grid. The objective is to form a horizontal, vertical, or diagonal line of three of their symbols to win the game. The app should also include a reset option to start a new game in python programming with emoji
ChatGPT said:
ChatGPT
Certainly! Here’s a README.md file for your Tic-Tac-Toe game app that includes emojis to make it more engaging:



# 🎮 Tic-Tac-Toe Game

Welcome to the **Tic-Tac-Toe Game**! This is a simple command-line Tic-Tac-Toe game built with Python. Players take turns placing their symbols (`X` and `O`) on a 3x3 grid. The goal is to create a line of three of your symbols horizontally, vertically, or diagonally. The game includes a reset option to start a new game. 🕹️

## Features

- 🧑‍🤝‍🧑 **Two-player mode**: Players alternate turns to place their symbols on the board.
- 🏆 **Win detection**: Automatically detects when a player has won or if the game ends in a draw.
- 🔄 **Reset and replay**: Offers the option to start a new game after one ends.

## Requirements

- Python 3.x 🐍

## Installation

1. **Clone the Repository**:


   git clone https://github.com/yourusername/tic-tac-toe.git
Navigate to the Project Directory:


cd tic-tac-toe
Usage
Run the Game:


python tic_tac_toe.py
Play the Game:

The game will prompt each player to enter the row and column (0, 1, or 2) where they want to place their symbol.
The current state of the game board will be displayed after each move.
The game will announce the winner or if the game is a draw.
After the game ends, you will be asked if you want to play again or exit.
Example
markdown

🎮 Your Tic-Tac-Toe Board:
 | | 
---------
 | | 
---------
 | | 

Player X's turn
Enter the row (0, 1, or 2): 0
Enter the column (0, 1, or 2): 1

🎮 Your Tic-Tac-Toe Board:
 | X | 
---------
 | | 
---------
 | | 

Player O's turn
Enter the row (0, 1, or 2): 1
Enter the column (1, 2, or 3): 1

🎮 Your Tic-Tac-Toe Board:
 | X | 
---------
 | O | 
---------
 | | 

Player X wins! 🏆
Do you want to play again? (y/n): n
Thank you for playing! Goodbye! 👋
Code Overview
tic_tac_toe.py: Contains the main code for the Tic-Tac-Toe game. Implements the game logic, displays the board, handles moves, and checks for a winner or draw.
License
This project is licensed under the MIT License. See the LICENSE file for details. 📝

Contributing
Feel free to fork the repository and submit pull requests. For bug reports or feature requests, please open an issue on GitHub. 🙌

Contact
For any questions or suggestions, you can reach out to your-email@example.com. 📧

Note: This is a basic implementation of Tic-Tac-Toe for educational purposes. For more advanced features, consider adding a graphical user interface (GUI) or AI opponents. 🛠️



### How to Use This README

1. **Replace Placeholder Text**: Update placeholders like `https://github.com/yourusername/tic-tac-toe.git` and `your-email@example.com` with your actual repository URL and contact information.
2. **Customize Further**: Adjust the content based on any additional features or changes to your project.

This `README.md` is designed to be both informative and engaging, using emojis to make the content visually appealing and easy to understand.
