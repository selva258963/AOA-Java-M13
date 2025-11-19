# EX 3E Generate Permutations using Backtracking  Approach.
## DATE:17/10/25
## AIM:
To write a Java program to for given constraints.
Given an array nums of distinct integers, return all the possible Permutation. You can return the answer in any order.
Example 1:
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
For example:
## Algorithm
1. Input array – Read the array of numbers from the user.

2. Initialize result list – Create a list to store all permutations.

3. Backtracking recursion – Build permutations by adding numbers not already in the current list.

4. Backtrack – After recursive call, remove the last number to explore other possibilities.

5. Output result – Print all generated permutations.

## Program:
```
/*
Program to implement Reverse a String
Developed by: Selvamuthu Kumaran V
Register Number: 212222040151

import java.util.*;

public class Solution {

    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        backtrack(new ArrayList<>(), ans, nums);
        return ans;
    }

    public void backtrack(List<Integer> curr, List<List<Integer>> ans, int[] nums) {
        // If current list is a full permutation, add it to result
        if (curr.size() == nums.length) {
            ans.add(new ArrayList<>(curr));
            return;
        }

        // Try each number if not already used
        for (int num : nums) {
            if (curr.contains(num)) continue; // skip if already included
            curr.add(num);
            backtrack(curr, ans, nums); // recursive call
            curr.remove(curr.size() - 1); // backtrack
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String inputLine = scanner.nextLine().trim();
        inputLine = inputLine.replaceAll(".*\\[|\\].*", ""); 
        String[] parts = inputLine.split(",");

        int[] nums = new int[parts.length];
        for (int i = 0; i < parts.length; i++) {
            nums[i] = Integer.parseInt(parts[i].trim());
        }

        Solution solution = new Solution();
        List<List<Integer>> permutations = solution.permute(nums);
        System.out.println(permutations);

        scanner.close();
    }
}

*/
```

## Output:

<img width="1076" height="165" alt="image" src="https://github.com/user-attachments/assets/ae1f1baf-ebcc-47bc-82c4-2c5d3cc5c528" />

## Result:
The program successfully implemented and the expected output is verified.
