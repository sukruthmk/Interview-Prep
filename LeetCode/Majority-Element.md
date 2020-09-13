# Majority Element

Given an array of size *n*, find the majority element. The majority element is the element that appears **more than** `⌊ n/2 ⌋` times.

You may assume that the array is non-empty and the majority element always exist in the array.

**Example 1:**

```
Input: [3,2,3]
Output: 3
```

**Example 2:**

```
Input: [2,2,1,1,1,2,2]
Output: 2
```



### Leetcode

https://leetcode.com/problems/majority-element/



### Optimal Solution

##### Approach 1 - HashMap

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function(nums) {
  const map = {};
  nums.sort();
  
  for(const num of nums) {
    map[num] = map[num] + 1 || 1;
    if(map[num] > nums.length / 2) {
      return num;
    }
  }
  
  // should not come here since the result always has a majority number
  return -1;
};
```



##### Approach 2 - Sorting

Time Complexity: O(nlogn)

Space Complexity: O(1)

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function(nums) {
  nums.sort();
  return nums[Math.floor(nums.length/2)];
};
```



##### Approach 3 - Boyer-Moore Voting Algorithm

Time Complexity: O(n)

Space Complexity: O(1)

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var majorityElement = function(nums) {
  let count = 0;
  let candidate = null;
  
  for(const num of nums) {
    if(count == 0) {
      candidate = num;
    }
    count += (num == candidate) ? 1 : -1;
  }
  
  return candidate;
};
```

