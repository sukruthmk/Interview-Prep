# Product Sum

Given an array `nums` of *n* integers where *n* > 1,  return an array `output` such that `output[i]` is equal to the product of all the elements of `nums` except `nums[i]`.

**Example:**

```
Input:  [1,2,3,4]
Output: [24,12,8,6]
```

**Constraint:** It's guaranteed that the product of the elements of any prefix or suffix of the array (including the whole array) fits in a 32 bit integer.

**Note:** Please solve it **without division** and in O(*n*).

**Follow up:**
Could you solve it with constant space complexity? (The output array **does not** count as extra space for the purpose of space complexity analysis.)



### Leetcode

https://leetcode.com/problems/product-of-array-except-self/



### Optimal Solution

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var productExceptSelf = function(nums) {
    const output = [];
    output[0] = 1;
    
    // calculate the left products without the current element
    for(let i=1; i<nums.length; i++) {
        output[i] = nums[i-1] * output[i-1];
    }
    
    // calculate right product using a variable
    // then multiply left products calculated in output with right product
    let right = 1;
    for(let i = nums.length - 1; i>=0; i--) {
        output[i] = output[i] * right;
        right  = right*nums[i];
    }
    
    return output;
};
```
