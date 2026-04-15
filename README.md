A simple Sudoku puzzle generator built in Java. This project generates a randomized Sudoku board using basic logic and prints it to the console.

Features:
Generates a valid 9x9 Sudoku board
Ensures rows, columns, and 3x3 boxes follow Sudoku rules
Randomized number placement for varied puzzles
Console-based output

How it works:
The program uses a backtracking algorithm to fill the Sudoku grid one cell at a time. It checks whether placing a number is valid based on:

Row constraints,
Column constraints,
3x3 subgrid constraints,
If a placement leads to a dead end, it tries a different number.

How to run:
Copy/Paste the repository and open the file and you should be able to run the program!
