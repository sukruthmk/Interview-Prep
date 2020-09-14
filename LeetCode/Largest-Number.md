# Largest Number

Given a list of non negative integers, arrange them such that they form the largest number.

**Example 1:**

```
Input: [10,2]
Output: "210"
```

**Example 2:**

```
Input: [3,30,34,5,9]
Output: "9534330"
```

**Note:** The result may be very large, so you need to return a string instead of an integer.



### Leetcode

https://leetcode.com/problems/largest-number/



### Optimal Solution

Time Complexity: O(nlogn)

Space Complexity: O(1)

```js
/**
 * @param {number[]} nums
 * @return {string}
 */
var largestNumber = function(nums) {
  nums.sort((a, b) => compare(a, b));
  
  // If, after sorting we get the largest number as zero the the number should be zero
  if (nums[0] == 0) {
      return "0";
  }
  
  return nums.join("");
};

const compare = (a, b) => {
  const strA = a.toString();
  const strB = b.toString();
  const order1 = strA + strB;
  const order2 = strB + strA;
  return order2.localeCompare(order1);
}
```
