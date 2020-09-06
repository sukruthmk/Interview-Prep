# First Missing Positive

Given an unsorted integer array, find the smallest missing positive integer.

**Example 1:**

```
Input: [1,2,0]
Output: 3
```

**Example 2:**

```
Input: [3,4,-1,1]
Output: 2
```

**Example 3:**

```
Input: [7,8,9,11,12]
Output: 1
```

**Follow up:**

Your algorithm should run in *O*(*n*) time and uses constant extra space.



### Leetcode

https://leetcode.com/problems/first-missing-positive/



### Optimal Solution

##### Approach 1 - HashMap

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var firstMissingPositive = function(nums) {
  // create a set for checking missing values
  const set = new Set(nums);
  
  // iterate from 1 to n-1
  for(let i=1; i<=nums.length; i++) {
    if(!set.has(i)) return i;
  }
  
  return nums.length + 1;
};
```



#####  Approach 2 - Array

Time Complexity: O(n)

Space Complexity: O(1)

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var firstMissingPositive = function(nums) {
  let i=0;
  
  while(i < nums.length) {
    const num = nums[i];
    
    // Ignore for these cases
    // 1. if negative number
    // 2. if nums[i] > nums.length
    // 3. if nums[i] == i+1 i.e the value is in right index ex:- nums[3] = 4
    // 4. if nums[nums[i]-1] == nums[i] to handle duplicates. 
    //    i.e we have already placed it in the right place
    if(num<=0 || num>nums.length || num == i+1 || nums[num-1] === num) {
      i++;
      continue;
    } 
    
    swap(nums, i, num - 1);
  }
  
  // find the index which is not having right value
  for(let i=0; i<nums.length; i++) {
    if(nums[i] != i+1) {
      return i+1;
    }
  }
  
  return nums.length + 1;
};

const swap = (nums, i, j) => {
  const temp = nums[i];
  nums[i] = nums[j];
  nums[j] = temp;
}
```



### Explanation

https://www.youtube.com/watch?v=2QugZILS_Q8