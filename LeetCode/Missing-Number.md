# Missing Number

Given an array containing *n* distinct numbers taken from `0, 1, 2, ..., n`, find the one that is missing from the array.

**Example 1:**

```
Input: [3,0,1]
Output: 2
```

**Example 2:**

```
Input: [9,6,4,2,3,5,7,0,1]
Output: 8
```

**Note**:
Your algorithm should run in linear runtime complexity. Could you implement it using only constant extra space complexity?



### Leetcode

https://leetcode.com/problems/missing-number/



### Optimal Solution

##### Approach 1 - Sorting

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var missingNumber = function(nums) {
  nums.sort((a, b) => a-b);
  
  if(nums[nums.length - 1] != nums.length) {
    return nums.length;
  } else if(nums[0] != 0) {
    return 0;
  }
  
  // If missing number is between (0, n);
  for(let i=1; i<nums.length; i++) {
    const num = nums[i-1] + 1;
    if(nums[i] != num) {
      return num;
    }
  }
  
  // Array is not missing any numbers
  return -1;
};
```



##### Approach 2 - HashMap

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var missingNumber = function(nums) {
  const set = new Set();
  
  // create the hashSet of nums
  for(const num of nums) {
    set.add(num);
  }
  
  for(let i=0; i<nums.length; i++) {
    if(!set.has(i)) return i;
  }
  
  return nums.length;
};
```
