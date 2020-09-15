# Happy Number

Write an algorithm to determine if a number `n` is "happy".

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it **loops endlessly in a cycle** which does not include 1. Those numbers for which this process **ends in 1** are happy numbers.

Return True if `n` is a happy number, and False if not.

**Example:** 

```
Input: 19
Output: true
Explanation: 
12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1
```



### Leetcode

https://leetcode.com/problems/happy-number/



### Optimal Solution

Time Complexity: 

Space Complexity: 

```js
/**
 * @param {number} n
 * @return {boolean}
 */
var isHappy = function(n) {
  const set = new Set();
  
  while(n != 1) {
    let current = n;
    let sum = 0;
    
    // iterate over each digit and get the squared digit sum
    while(current != 0) {
      const digit = current % 10;
      sum += digit*digit;
      current = Math.floor(current/10)
    }
    
    // not a happy number if it is in a cycle
    if(set.has(sum)) return false;
    
    set.add(sum);
    n = sum;
  } 
  
  return true;
};
```



### Explanation

https://www.youtube.com/watch?v=gW4hSbRoQoY