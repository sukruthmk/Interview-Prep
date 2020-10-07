# Shuffle an Array

Shuffle a set of numbers without duplicates.

**Example:**

```
// Init an array with set 1, 2, and 3.
int[] nums = {1,2,3};
Solution solution = new Solution(nums);

// Shuffle the array [1,2,3] and return its result. Any permutation of [1,2,3] must equally likely to be returned.
solution.shuffle();

// Resets the array back to its original configuration [1,2,3].
solution.reset();

// Returns the random shuffling of array [1,2,3].
solution.shuffle();
```



### Leetcode

https://leetcode.com/problems/shuffle-an-array/



### Optimal Solution

Time Complexity: O(n)

Space Complexity: O(1)

```js
/**
 * @param {number[]} nums
 */

class Solution {
  constructor(nums) {
    this.nums = [...nums];
  }
  
  reset() {
    // return the original array
    return this.nums;
  }
  
  shuffle() {
    // 1. clone the array
    const nums = [...this.nums];
    const length = nums.length;
    
    // 2. iterate over each items and swap it with a random element in the array
    for(let i=0; i<length; i++) {
      // get the random index to swap in the array
      const j = Math.floor(length * Math.random());
      const temp = nums[i];
      nums[i] = nums[j];
      nums[j] = temp;
    }
    
    return nums;
  }
}
```



### Explanation

https://www.youtube.com/watch?v=CoI4S7z1E1Y

