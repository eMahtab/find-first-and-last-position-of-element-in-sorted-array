# Find first and last position of element in sorted array
## https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array

Given an array of integers nums sorted in ascending order, find the starting and ending position of a given target value.

Your algorithm's runtime complexity must be in the order of O(log n).

If the target is not found in the array, return [-1, -1].
```
Example 1:

Input: nums = [5,7,7,8,8,10], target = 8
Output: [3,4]

Example 2:

Input: nums = [5,7,7,8,8,10], target = 6
Output: [-1,-1]

Example 3:

Input: nums = [5,7,7,8,8,10], target = 10
Output: [5,5]
```

**Constraints:**

1. 0 <= nums.length <= 10^5
2. -10^9 <= nums[i] <= 10^9
3. nums is a non decreasing array.
4. -10^9 <= target <= 10^9

## Approach :
We can easily solve this question in O(n), but since the array is sorted we should use binary search to solve this problem in O(logn).

So first we will find the index of the first occurance of `target`
And if the index of first occurance of target is not `-1`, it means `target` exists in the array.
Next we will find the index of the last occurance of `target`
