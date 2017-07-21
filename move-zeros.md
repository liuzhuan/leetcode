# 283. [Move Zeros](https://leetcode.com/problems/move-zeroes/#/description)

## Description

Given an array `nums`, write a function to move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.

For example, given `nums = [0, 1, 0, 3, 12]`, after calling your function, `nums` should be `[1, 3, 12, 0, 0]`.

**Note:**

1. You must do this **in-place** without making a copy of the array.
2. Minimize the total number of operations.

**Credits:**
Special thanks to [@jianchao.li.fighter](https://leetcode.com/discuss/user/jianchao.li.fighter) for adding this problem and creating all test cases.

## My Solution

```javascript
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function(nums) {
    var n = nums.length - 1;
    for (var i = n; i >= 0; i--) {
      if (nums[i] === 0 && i < n && nums[i+1] !== 0) {
        nums.splice(i, 1);
        nums.push(0);
      }
    }
};
```

Status: **Accepted**

Runtime: **125 ms**

## Sample 105 ms submission 

```javascript
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function(nums) {
    var N = nums.length, i = 0, j = 0;
    while(j < N) {
        if(nums[j] !== 0) {
            nums[i++] = nums[j];
        }
        j++;
    }
    while(i < N) nums[i++] = 0;
};
```

> 赋值和双指针操作效率高