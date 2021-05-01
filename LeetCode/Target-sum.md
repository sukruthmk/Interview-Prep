# Target Sum

You are given an integer array `nums` and an integer `target`.

You want to build an **expression** out of nums by adding one of the symbols `'+'` and `'-'` before each integer in nums and then concatenate all the integers.

- For example, if `nums = [2, 1]`, you can add a `'+'` before `2` and a `'-'` before `1` and concatenate them to build the expression `"+2-1"`.

Return the number of different **expressions** that you can build, which evaluates to `target`.

 

**Example 1:**

```
Input: nums = [1,1,1,1,1], target = 3
Output: 5
Explanation: There are 5 ways to assign symbols to make the sum of nums be target 3.
-1 + 1 + 1 + 1 + 1 = 3
+1 - 1 + 1 + 1 + 1 = 3
+1 + 1 - 1 + 1 + 1 = 3
+1 + 1 + 1 - 1 + 1 = 3
+1 + 1 + 1 + 1 - 1 = 3
```

**Example 2:**

```
Input: nums = [1], target = 1
Output: 1
```

 

**Constraints:**

- `1 <= nums.length <= 20`
- `0 <= nums[i] <= 1000`
- `0 <= sum(nums[i]) <= 1000`
- `-1000 <= target <= 1000`



### Leetcode

https://leetcode.com/problems/target-sum/



### Optimal Solution

Time Complexity: *O(l⋅n)* The memo array of size l*n has been filled just once. Here, l refers to the range of sum and n refers to the size of nums array.

Space Complexity: *O(l⋅n)* The depth of recursion tree can go upto *n*. The memo array contain l*n elements.

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var findTargetSumWays = function (nums, target) {
  // 1. memoization initialization
  let memo = new Map();

  const findWays = (nums, target, i, currSum) => {
    if (i > nums.length - 1) {
      if (target === currSum) {
        return 1;
      }
      return 0;
    }

    const token = i + "->" + currSum;
    if (memo.get(token)) {
      return memo.get(token);
    }

    const num = nums[i];
    const add = findWays(nums, target, i + 1, currSum + num);
    const subtract = findWays(nums, target, i + 1, currSum - num);
    if (!memo.get(token)) {
      memo.set(token, add + subtract);
    }
    return memo.get(token);
  };

  return findWays(nums, target, 0, 0);
};
```

