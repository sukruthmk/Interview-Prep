# Two Number Sum

Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.

You may assume that each input would have **\*exactly\*** one solution, and you may not use the _same_ element twice.

**Example:**

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

## Leetcode

<https://leetcode.com/problems/two-sum/>

## Solution

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function (nums, target) {
  const n = nums.length;
  const map = {};
  for (let i = 0; i < n; i++) {
    const value = nums[i];
    const find = target - value;
    if (typeof map[find] != "undefined") {
      return [map[find], i];
    }
    if (!map[value]) {
      map[value] = i;
    }
  }
  return [];
};
```
