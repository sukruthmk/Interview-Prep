# Find the Duplicate Number

Given an array of integers `nums` containing `n + 1` integers where each integer is in the range `[1, n]` inclusive.

There is only **one duplicate number** in `nums`, return *this duplicate number*.

**Follow-ups:**

1. How can we prove that at least one duplicate number must exist in `nums`? 
2. Can you solve the problem **without** modifying the array `nums`?
3. Can you solve the problem using only constant, `O(1)` extra space?
4. Can you solve the problem with runtime complexity less than `O(n2)`?

 

**Example 1:**

```
Input: nums = [1,3,4,2,2]
Output: 2
```

**Example 2:**

```
Input: nums = [3,1,3,4,2]
Output: 3
```

**Example 3:**

```
Input: nums = [1,1]
Output: 1
```

**Example 4:**

```
Input: nums = [1,1,2]
Output: 1
```

 

**Constraints:**

- `2 <= n <= 3 * 104`
- `nums.length == n + 1`
- `1 <= nums[i] <= n`
- All the integers in `nums` appear only **once** except for **precisely one integer** which appears **two or more** times.



### Leetcode

https://leetcode.com/problems/find-the-duplicate-number/



### Optimal Solution

##### Approach 1 - Set

Time Complexity: O(n)

Space Complexity: O(1)

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var findDuplicate = function(nums) {
  const set = new Set();
  
  for(const num of nums) {
    if(set.has(num)) {
      return num;
    }
    set.add(num);
  }
  
  return -1;
};
```



##### Approach 2 -  Floyd's Tortoise and Hare (Cycle Detection)

Time Complexity: O(n)

Space Complexity: O(1)

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var findDuplicate = function(nums) {
  let slow = nums[0];
  let fast = nums[0];
  
  // find the intersection point of the two runners.
  do {
    slow = nums[slow];
    fast = nums[nums[fast]];
  } while(slow != fast);
  
  // find the starting point of the cycle.
  slow = nums[0];
  while(slow != fast) {
    slow = nums[slow];
    fast = nums[fast];
  }
  
  return fast;
};
```



### Explanation

https://www.youtube.com/watch?v=i4kBcvA3OV4