
# EX 3A N Queens Problem - Backtracking Approach.
## DATE:15/10/25
## AIM:
To Write a Java program for N queens using backtracking approach.
You are given an integer N. For a given N x N chessboard, find a way to place 'N' queens such that no queen can attack any other queen on the chessboard.
A queen can be attacked when it lies in the same row, column, or the same diagonal as any of the other queens. You have to print one such configuration.
Chess Board
<img width="241" height="209" alt="image" src="https://github.com/user-attachments/assets/96aacb61-4f34-423f-b324-5e34454e42b8" />


Note :

Get the input from the user for N . The value of N must be from 1 to 4

If solution exists Print a binary matrix as output that has 1s for the cells where queens are placed

If there is no solution to the problem  print  "Solution does not exist"

## Algorithm
1.Input N – Read the board size from the user.

2.Initialize board – Create an N×N board with all 0s.

3.Check safety – Verify if a queen can be placed without attack.

4.Place queens – Use recursion and backtracking to place queens column by column.

5.Output result – Print the board if solved; else print “Solution does not exist.” 

## Program:
```
/*
N Queens Problem - Backtracking Approach.
Developed by: Selvamuthu Kumaran V
Register Number: 212222040151  

import java.util.Scanner;

public class NQueens {
    static int N;

    static void printSolution(int[][] board) {
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++) {
                System.out.print(board[i][j] + " ");
            }
            System.out.println();
        }
    }

    static boolean isSafe(int[][] board, int row, int col) {
        // Check this row on the left
        for (int i = 0; i < col; i++)
            if (board[row][i] == 1)
                return false;

        // Check upper diagonal on the left
        for (int i = row, j = col; i >= 0 && j >= 0; i--, j--)
            if (board[i][j] == 1)
                return false;

        // Check lower diagonal on the left
        for (int i = row, j = col; i < N && j >= 0; i++, j--)
            if (board[i][j] == 1)
                return false;

        return true;
    }

    static boolean solveNQUtil(int[][] board, int col) {
        // Base case: if all queens are placed
        if (col >= N)
            return true;

        // Try placing queen in all rows one by one
        for (int i = 0; i < N; i++) {
            if (isSafe(board, i, col)) {
                board[i][col] = 1; // place queen

                if (solveNQUtil(board, col + 1)) // recursive call
                    return true;

                board[i][col] = 0; // backtrack
            }
        }
        return false; // if no position is possible
    }

    static boolean solveNQ() {
        int[][] board = new int[N][N];

        if (!solveNQUtil(board, 0)) {
            System.out.println("Solution does not exist");
            return false;
        }

        printSolution(board);
        return true;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        N = scanner.nextInt();

        // Since only 1 to 4 is allowed
        if (N < 1 || N > 4) {
            System.out.println("Solution does not exist");
        } else {
            solveNQ();
        }
    }
}

*/
```

## Output:

<img width="627" height="270" alt="image" src="https://github.com/user-attachments/assets/077de624-120c-4655-8206-6e5302ebed4a" />

## Result:
The program successfully implemented and the ouput is verified. 
