# EX 3C Tug of War problem - Backtracking.
## DATE:10/10/25
## AIM:
To write a Java program to for given constraints.
Given an integer array nums, return true if you can partition the array into two subsets such that the sum of the elements in both subsets is equal or false otherwise.
Example 1:
Input: Enter the number of elements: 4
Enter the elements of the array:
1 5 11 5
Output: true
Explanation: The array can be partitioned as [1, 5, 5] and [11].

Constraints:

1 <= nums.length <= 200
1 <= nums[i] <= 100

## Algorithm
1. Input array – Read the number of elements and the array values.

2. Calculate total sum – Sum all elements in the array.

3. Check feasibility – If total sum is odd, return false (cannot partition).

4. Dynamic Programming – Use a boolean DP array to check if a subset sums to half of total.

5. Return result – If DP[target] is true, array can be partitioned; else false.

## Program:
```
/*
Tug of War problem - Backtracking
Developed by: Selvamuthu Kumaran V
Register Number: 212222040151

import java.util.Scanner;
public class Solution {
    public boolean canPartition(int[] nums) {
        //Type your code here
        int totalSum=0;
        for (int num : nums) {
            totalSum += num;
        }
        
        if (totalSum % 2 != 0) {
            return false;
        }
        
        int target = totalSum / 2;
        boolean[] dp = new boolean[target + 1];
        dp[0] = true;
        
        for (int num : nums) {
            for (int j = target; j >= num; j--) {
                dp[j] = dp[j] || dp[j - num];
            }
        }
        
        return dp[target];
    }
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution sol = new Solution();
        int n = scanner.nextInt();
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = scanner.nextInt();
        }
        boolean canBePartitioned = sol.canPartition(nums);
        System.out.println(canBePartitioned);
    }
}
*/
```

## Output:

<img width="396" height="227" alt="image" src="https://github.com/user-attachments/assets/acceb1d7-a3a1-4588-a00b-a739d1a634fe" />


## Result:
The program successfully implemented and the expected output is verified.
