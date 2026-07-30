# Bash Typing Game

A simple interactive typing game built using Bash scripting and Linux.

This project was created to practice Bash scripting concepts by building a small
command-line game with menus, different game modes, typing rounds, scoring,
accuracy calculation, and score tracking.

## Project Overview

The Bash Typing Game allows the user to choose a game mode and type randomly
selected words or sentences within the game.

The game evaluates the user's typing performance and calculates information
such as typing speed, accuracy, and score.

It also stores scores in a local file so that previous game results can be
kept for future reference.

## Features

- Interactive command-line menu
- Multiple game modes
- Different typing rounds
- Random typing challenges
- Score calculation
- Typing speed calculation
- Accuracy calculation
- Score history
- User input handling
- Simple terminal-based interface
- Colored terminal output

## Game Flow

The game follows a simple flow:

1. Start the Bash script.
2. The main menu is displayed.
3. Select a game mode.
4. The game starts a typing round.
5. A word or sentence is displayed.
6. Type the displayed text.
7. The game checks the input.
8. Score and typing performance are calculated.
9. The next round starts.
10. The final score is displayed.
11. The score can be saved for future reference.

## Technologies Used

- Bash
- Linux
- Shell scripting
- Terminal

## Bash Concepts Used

This project helped me practice several Bash scripting concepts:

### Functions

Functions are used to divide the game into smaller reusable sections.

Examples include:

- Menu functions
- Game functions
- Round functions
- Score-related functions

### Variables

Variables are used to store:

- User input
- Scores
- Typing speed
- Accuracy
- Game settings
- File locations

### Conditional Statements

`if`, `elif`, and `else` statements are used to make decisions based on
the user's input and game results.

### Loops

Loops are used to repeat typing rounds and keep the game running until the
user chooses to exit.

### User Input

The `read` command is used to receive input from the player.

### File Handling

The game uses a local score file to store game results and maintain score
history.

### String Handling

Bash string operations are used to compare the user's input with the
expected text and calculate typing results.

### Terminal Formatting

ANSI escape sequences are used to add colors and improve the appearance
of the game in the terminal.

## How to Run

Clone the repository:

git clone https://github.com/farisneendoor/Devops_Scripting-/blob/main/Shell%20-%20Typing%20Game/Typing%20Game.sh
