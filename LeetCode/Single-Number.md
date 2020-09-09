# Single Number

Given a **non-empty** array of integers, every element appears *twice* except for one. Find that single one.

**Note:**

Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

**Example 1:**

```
Input: [2,2,1]
Output: 1
```

**Example 2:**

```
Input: [4,1,2,1,2]
Output: 4
```



### Leetcode

https://leetcode.com/problems/single-number/



### Optimal Solution

##### Approach 1 - HashMap

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
  const map = {};
  
  // create a hasMap with frequency of repitions
  for(const num of nums) {
    map[num] = map[num] ? map[num] + 1 : 1;
  }
  
  // iterate and find the value with frequency one
  const keys = Object.keys(map);
  for(const key of keys) {
    if(map[key] === 1) {
      return key;
    }
  }
  
  return 0;
};
```



##### Approach 2 - Math

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
  const set = new Set();
  let sumOfSet = 0;
  let sumOfNums = 0;
  
  for(const num of nums) {
    if(!set.has(num)) {
      set.add(num);
      sumOfSet += num;
    }
    sumOfNums += num;
  }
  
  return 2*sumOfSet - sumOfNums;
};
```



##### Approach 3 - Bit Manipulation

Time Complexity: O(n)

Space Complexity: O(1)

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
  let bit = 0;
  // XOR
  for(const num of nums) {
    bit ^= num;
  }
  return bit;
};
```

