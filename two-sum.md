# 1. [Two Sum](https://leetcode.com/problems/two-sum/#/description)

## Description

Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.

You may assume that each input would have **exactly** one solution, and you may not use the *same* element twice.

**Example:**

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```
## My Solution

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
 
 var twoSum = function(nums, target) {
     if (!nums || nums.length < 2) return;
     
     for (var a = 0; a < nums.length - 1; a += 1) {
         for (var b = a + 1; b < nums.length; b += 1) {
             if (nums[a] + nums[b] === target) {
                 return [a, b];
             }
         }
     }
 }
```

Status: **Accepted**

Runtime: **209 ms**

## Sample 92ms submission

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
    var obj = {};
    
    for (var i = 0; i < nums.length; i++) {
        var diff = target - nums[i];
        if (obj.hasOwnProperty(diff)) {
            return [obj[diff] , i]
        } else {
            obj[nums[i]] = i; 
        }
    }
};
```

> Object 字典缓存提升查询速度。