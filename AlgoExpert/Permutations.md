# Permutations

Given a collection of **distinct** integers, return all possible permutations.

**Example:**

```
Input: [1,2,3]
Output:
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```



### Leetcode

https://leetcode.com/problems/permutations/



### Optimal Solution

Time Complexity: O(n!*n)

```js
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var permute = function(nums) {
  const result = [];
  findPermutations(nums, result, 0);
  return result;
};

const findPermutations = (nums, result, i) => {
  // base case if we reached the end
  if (i === nums.length - 1) {
    // use spread operator to clone since nums will be stored as reference. 
    result.push([...nums]);
    return;
  }

  // iterate from j=i to nums.length
  for (let j = i; j < nums.length; j++) {
    // swap first
    swap(nums, i, j);
    // permute remaining
    findPermutations(nums, result, i + 1);
    // after done put it back to same place 
    // so that input is not changed
    swap(nums, i, j);
  }
}

// helper function to swap numbers in the positon i and j
const swap = (nums, i, j) => {
  const temp = nums[i];
  nums[i] = nums[j];
  nums[j] = temp;
}
```

