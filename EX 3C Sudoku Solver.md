# EX 3C Sudoku Solver
## DATE:
## AIM:
To write a python program to find the solution of sudoku puzzle using Backtracking.


## Algorithm
1. Find the first empty cell (cell with 0) in the Sudoku board.
2. Try placing numbers 1 to 9 in that empty cell.
3. For each number, check if it is safe (valid) to place by row, column, and 3×3 box rules.
4. If safe, place the number and recursively attempt to fill the next empty cell.
5. If the board is completely filled without conflicts, print the solution. 

## Program:
```
Program to implement to to find the solution of sudoku puzzle using Backtracking.
Developed by: Vinush CV
Register Number: 212222230176
```
```python
board = [
    [0, 0, 0, 8, 0, 0, 4, 0, 3],
    [2, 0, 0, 0, 0, 4, 8, 9, 0],
    [0, 9, 0, 0, 0, 0, 0, 0, 2],
    [0, 0, 0, 0, 2, 9, 0, 1, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 7, 0, 6, 5, 0, 0, 0, 0],
    [9, 0, 0, 0, 0, 0, 0, 8, 0],
    [0, 6, 2, 7, 0, 0, 0, 0, 1],
    [4, 0, 3, 0, 0, 6, 0, 0, 0]
]

def printBoard(board):
    for i in range(0, 9):
        for j in range(0, 9):
            print(board[i][j], end=" ")
        print()

def isPossible(board, row, col, val):
    for j in range(0, 9):
        if board[row][j] == val:
            return False

    for i in range(0, 9):
        if board[i][col] == val:
            return False

    startRow = (row // 3) * 3
    startCol = (col // 3) * 3
    for i in range(0, 3):
        for j in range(0, 3):
            if board[startRow+i][startCol+j] == val:
                return False
    return True

def solve():
    #####################  Add your code here #########################
    for i in range(0, 9):
        for j in range(0, 9):
            if board[i][j] == 0:
                for val in range(1, 10):
                    if isPossible(board, i, j, val):
                        board[i][j] = val
                        if solve():  
                            return True
                        board[i][j] = 0  
                return False
    return True
    
solve()
printBoard(board)

```

## Output:
![image](https://github.com/user-attachments/assets/b12f5fb7-18a2-4345-9caf-c5743b51abef)



## Result:
The Sudoku solver program executed successfully and found the solution for the given puzzle.
