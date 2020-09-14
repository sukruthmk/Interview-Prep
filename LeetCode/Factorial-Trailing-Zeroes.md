# Factorial Trailing Zeroes

Given an integer *n*, return the number of trailing zeroes in *n*!.

**Example 1:**

```
Input: 3
Output: 0
Explanation: 3! = 6, no trailing zero.
```

**Example 2:**

```
Input: 5
Output: 1
Explanation: 5! = 120, one trailing zero.
```

**Note:** Your solution should be in logarithmic time complexity.



### Leetcode

https://leetcode.com/problems/factorial-trailing-zeroes/



### Optimal Solution

Time Complexity: O(logN)

Space Complexity: O(1)

```js
/**
 * @param {number} n
 * @return {number}
 */
var trailingZeroes = function(n) {
    let numOfFives = 0;
    
    while(n >= 5) {
        const multiple = Math.floor(n/5);
        numOfFives += multiple;
        n = multiple;
    }
    
    return numOfFives;
};
```



### Explanation

https://www.youtube.com/watch?v=3Hdmv_Ym8PI