# Intersection of Two Arrays II

Given two arrays, write a function to compute their intersection.

**Example 1:**

```
Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2,2]
```

**Example 2:**

```
Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Output: [4,9]
```

**Note:**

- Each element in the result should appear as many times as it shows in both arrays.
- The result can be in any order.

**Follow up:**

- What if the given array is already sorted? How would you optimize your algorithm?
- What if *nums1*'s size is small compared to *nums2*'s size? Which algorithm is better?
- What if elements of *nums2* are stored on disk, and the memory is limited such that you cannot load all elements into the memory at once?



### Leetcode

https://leetcode.com/problems/intersection-of-two-arrays-ii/



### Optimal Solution

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersect = function(nums1, nums2) {
  const map = {};
  const result = [];
  
  // 1. create a hashMap and store the frequency of repition
  for(const num of nums1) {
    map[num] = map[num] ? map[num] + 1 : 1;
  }
  
  // 2. foreach number in nums2 add the common ones to the array
  for(const num of nums2) {
    if(map[num] > 0) {
      result.push(num);
      map[num] = map[num] - 1;
    }
  }
    
  return result;
};
```
