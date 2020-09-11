# Maximum Product Subarray

Given an integer array `nums`, find the contiguous subarray within an array (containing at least one number) which has the largest product.

**Example 1:**

```
Input: [2,3,-2,4]
Output: 6
Explanation: [2,3] has the largest product 6.
```

**Example 2:**

```
Input: [-2,0,-1]
Output: 0
Explanation: The result cannot be 2, because [-2,-1] is not a subarray.
```



### Leetcode

https://leetcode.com/problems/maximum-product-subarray/



### Optimal Solution

Time Complexity: O(n)

Space Complexity: O(1)

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var maxProduct = function(nums) {
  if(nums.length === 0) return 0;
  
  let currentMax = nums[0];
  let currentMin = nums[0];
  let finalMax = nums[0];
  
  for(let i=1; i<nums.length; i++) {
    const num = nums[i];
    const maxProduct = currentMax * num;
    const minProduct = currentMin * num;
    
    // keep track both max and min products
    // because -12 * -2 = 24
    currentMax = Math.max(Math.max(maxProduct, minProduct), num);
    currentMin = Math.min(Math.min(maxProduct, minProduct), num);
    
    if(currentMax > finalMax) {
      finalMax = currentMax;
    }
  }
  
  return finalMax;
};
```



### Explanation

https://www.youtube.com/watch?v=1s0r7Ixir80