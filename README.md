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

## Implementation : Time Complexity : O(logn)
```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        if(nums == null)
            return new int[]{-1, -1};
        
        int firstIndex = findFirst(nums, target);
        if(firstIndex == -1)
            return new int[]{-1, -1};
        
        int lastIndex = findLast(nums, target, firstIndex);
        return new int[] {firstIndex, lastIndex};
    }
    
    // [1, 2, 3, 4, 5, 5, 6] , target = 5 , it will return 4
    // [1, 2, 3, 4, 4, 5, 6, 7, 8]  , target = 4, it will return 3
    private int findFirst(int[] nums, int target) {
        int left = 0, right = nums.length - 1;
        int firstIndex = -1;
        
        while(left <= right) {
            int mid = left + (right-left) / 2;
            if(nums[mid] == target) {
                firstIndex = mid;
                right = mid - 1;
            } else if(nums[mid] > target) {
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        }
        return firstIndex;
    }
    
    private int findLast(int[] nums, int target, int firstIndex) {
        int left = firstIndex, right = nums.length - 1;
        int lastIndex = firstIndex;
        
        while(left <= right) {
            int mid = left + (right - left) / 2;
            if(nums[mid] == target) {
                lastIndex = mid;
                left = mid + 1;
            } else if (nums[mid] > target) {
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        }
        return lastIndex;
    }
}
```

# References :
https://www.youtube.com/watch?v=EwggFsMTxu8
