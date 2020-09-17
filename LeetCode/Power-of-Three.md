# Power of Three

Given an integer, write a function to determine if it is a power of three.

**Example 1:**

```
Input: 27
Output: true
```

**Example 2:**

```
Input: 0
Output: false
```

**Example 3:**

```
Input: 9
Output: true
```

**Example 4:**

```
Input: 45
Output: false
```

**Follow up:**
Could you do it without using any loop / recursion?



### Leetcode

https://leetcode.com/problems/power-of-three/



### Optimal Solution

Time Complexity: 

Space Complexity: 

```js
/**
 * @param {number} n
 * @return {boolean}
 */
var isPowerOfThree = function(n) {
  if(n === 0) return false;
  return helper(n);
};

const helper = (num) => {
  if(num === 1) return true;
  if(num %3 != 0) return false;
  
  return helper(num/3);
}
```
