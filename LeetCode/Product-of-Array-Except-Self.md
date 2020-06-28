# Product of Array Except Self

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

Space Complexity: O(n)  - because of extra arrays leftProducts and rightProducts

```js
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var productExceptSelf = function(nums) {
    const leftProducts = [];
    const rightProducts = [];
    const output = [];
    
    leftProducts[0] = 1;
    rightProducts[nums.length - 1] = 1;
    
    // calculate the left products without the current element
    for(let i=1; i<nums.length; i++) {
        leftProducts[i] = nums[i-1] * leftProducts[i-1];
    }
    
    // calculate right products without the current element
    for(let i=nums.length - 2; i>=0; i--) {
        rightProducts[i] = nums[i+1] * rightProducts[i+1];
    }
    
    // multiply left products with right products to get the result
    for(let i=0; i<nums.length; i++) {
        output[i] = leftProducts[i] * rightProducts[i];
    }
    
    return output;
};
```



Time Complexity: O(n)

Space Complexity: O(1)  - output array is not considered as extra space according to the question.

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



### Explanation

https://www.youtube.com/watch?v=tSRFtR3pv74