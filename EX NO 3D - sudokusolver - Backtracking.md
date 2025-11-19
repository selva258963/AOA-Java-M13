# EX 3D Sudoku solver - Backtracking.
## DATE:15/10/25
## AIM:
To write a Java program to solve a Sudoku puzzle by filling the empty cells.

For example:
<img width="357" height="322" alt="image" src="https://github.com/user-attachments/assets/334b8c39-d547-4743-aca0-de92e38bdd1c" />



## Algorithm
1. Input board – Read the 9×9 Sudoku grid from the user.

2. Check safety – For a cell, verify the number is not in the same row, column, or 3×3 subgrid.

3. Recursive placement – Try placing numbers 1–9 in empty cells recursively.

4. Backtracking – If no number fits, reset the cell to 0 and backtrack.

5. Output result – Print the solved board if possible; else print “No solution exists.”

## Program:
```
/*
Sudoku solver - Backtracking
Developed by: Selvamuthu Kumaran V
Register Number: 212222040151

import java.util.Scanner;

public class SudokuSolver {

    // Check if it's safe to place the number
    static boolean isSafe(int[][] board, int row, int col, int num) {
        // Check row and column
        for (int i = 0; i < 9; i++) {
            if (board[row][i] == num || board[i][col] == num)
                return false;
        }

        // Check 3x3 subgrid
        int startRow = row - row % 3;
        int startCol = col - col % 3;

        for (int i = 0; i < 3; i++)
            for (int j = 0; j < 3; j++)
                if (board[startRow + i][startCol + j] == num)
                    return false;

        return true;
    }

    // Recursive backtracking solver
    static boolean solveSudoku(int[][] board, int row, int col) {
        // if reached end of board
        if (row == 9)
            return true;

        // move to next row if col=9
        if (col == 9)
            return solveSudoku(board, row + 1, 0);

        // if already filled, move forward
        if (board[row][col] != 0)
            return solveSudoku(board, row, col + 1);

        // try digits 1 to 9
        for (int num = 1; num <= 9; num++) {
            if (isSafe(board, row, col, num)) {
                board[row][col] = num;

                if (solveSudoku(board, row, col + 1))
                    return true;

                // backtrack
                board[row][col] = 0;
            }
        }

        return false; // no number fits
    }

    // Utility to print the board
    static void printBoard(int[][] board) {
        for (int[] row : board) {
            for (int val : row)
                System.out.print(val + " ");
            System.out.println();
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int[][] board = new int[9][9];

        for (int i = 0; i < 9; i++) {
            for (int j = 0; j < 9; j++) {
                board[i][j] = sc.nextInt();
            }
        }

        if (solveSudoku(board, 0, 0)) {
            System.out.println("Solved Sudoku:");
            printBoard(board);
        } else {
            System.out.println("No solution exists.");
        }

        sc.close();
    }
}

*/
```

## Output:

<img width="681" height="611" alt="image" src="https://github.com/user-attachments/assets/4949b8a8-4336-4dc6-87be-b1443f553a31" />

## Result:
The program successfully implemented and the expected output is verified.
