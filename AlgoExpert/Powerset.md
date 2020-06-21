# Powerset

Given a set of **distinct** integers, *nums*, return all possible subsets (the power set).

**Note:** The solution set must not contain duplicate subsets.

**Example:**

```
Input: nums = [1,2,3]
Output:
[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]
```



### Leetcode

https://leetcode.com/problems/subsets/



### Optimal Solution

Time Complexity: O(n*2^n)

Space Complexity: O(n*2^n)

```js
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var subsets = function(nums) {
    const subsets = [];
    generateSubsets(nums, 0, subsets, []);
    return subsets;
}

const generateSubsets = (nums, i, subsets, current) => {
    subsets.push(current.slice());
    for(let j = i; j < nums.length; j++) {
        current.push(nums[j]);
        // generate all other subsets for the current subset.
        // increasing the position by one to avoid duplicates in 'result'
        generateSubsets(nums, j+1, subsets, current);
        current.pop();
    }
}
```

