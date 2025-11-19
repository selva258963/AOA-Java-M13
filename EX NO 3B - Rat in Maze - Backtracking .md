
# EX 3B Rat in Maze- Backtracking 
## DATE:
## AIM:
To write a Java program to for given constraints.
here is a ball in a maze with empty spaces (represented as 0) and walls (represented as 1). The ball can go through the empty spaces by rolling up, down, left or right, but it won't stop rolling until hitting a wall. When the ball stops, it could choose the next direction.

Given the m x n maze, the ball's start position and the destination, where start = [startrow, startcol] and destination = [destinationrow, destinationcol], return true if the ball can stop at the destination, otherwise return false.

You may assume that the borders of the maze are all walls (see examples).
<img width="573" height="573" alt="image" src="https://github.com/user-attachments/assets/d6f1c054-cdc2-4bb3-9c55-512fb2cf0fb7" />
Input: maze = [[0,0,1,0,0],[0,0,0,0,0],[0,0,0,1,0],[1,1,0,1,1],[0,0,0,0,0]], start = [0,4], destination = [4,4]
Output: true
Explanation: One possible way is : left -> down -> left -> down -> right -> down -> right.


## Algorithm
1. Input maze – Read the maze dimensions, cells, start, and destination positions.

2. Initialize visited array – Create a boolean array to track visited cells.

3. DFS traversal – From the current cell, explore all four directions recursively.

4. Roll until wall – Move in one direction until hitting a wall, then recurse from the stopping point.

5. Check destination – Return true if destination is reached; otherwise, backtrack and continue.

## Program:
```
/*
Rat in Maze- Backtracking 
Developed by: Selvamuthu Kumaran V
Register Number:  212222040151
*/

import java.util.*;

public class Main {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Read maze dimensions
        int m = sc.nextInt();
        int n = sc.nextInt();

        int[][] maze = new int[m][n];
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                maze[i][j] = sc.nextInt();
            }
        }

        // Read start position
        int[] start = new int[]{sc.nextInt(), sc.nextInt()};

        // Read destination position
        int[] destination = new int[]{sc.nextInt(), sc.nextInt()};

        Solution sol = new Solution();
        boolean result = sol.hasPath(maze, start, destination);

        System.out.println(result);
    }
}

class Solution {
    // DFS helper function
    public boolean dfs(int m, int n, int[][] maze, int[] curr, int[] destination, boolean[][] visit) {
        // If already visited, skip
        if (visit[curr[0]][curr[1]]) return false;

        // Mark current cell as visited
        visit[curr[0]][curr[1]] = true;

        // Check if reached destination
        if (curr[0] == destination[0] && curr[1] == destination[1])
            return true;

        // Directions: up, down, left, right
        int[][] dirs = {{-1, 0}, {1, 0}, {0, -1}, {0, 1}};

        for (int[] dir : dirs) {
            int x = curr[0];
            int y = curr[1];

            // Roll the ball until it hits a wall
            while (x + dir[0] >= 0 && x + dir[0] < m &&
                   y + dir[1] >= 0 && y + dir[1] < n &&
                   maze[x + dir[0]][y + dir[1]] == 0) {
                x += dir[0];
                y += dir[1];
            }

            // Recurse from the stopping position
            if (dfs(m, n, maze, new int[]{x, y}, destination, visit))
                return true;
        }

        return false;
    }

    // Main function
    public boolean hasPath(int[][] maze, int[] start, int[] destination) {
        int m = maze.length;
        int n = maze[0].length;
        boolean[][] visit = new boolean[m][n];

        return dfs(m, n, maze, start, destination, visit);
    }
}

```

## Output:

<img width="356" height="526" alt="image" src="https://github.com/user-attachments/assets/5c8cc470-efb8-4dbc-bf4f-e1df6932d3bb" />


## Result:
The program successfully implemented and the expected output is verified.
