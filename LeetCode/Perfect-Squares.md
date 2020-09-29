# Perfect Squares

Given a positive integer *n*, find the least number of perfect square numbers (for example, `1, 4, 9, 16, ...`) which sum to *n*.

**Example 1:**

```
Input: n = 12
Output: 3 
Explanation: 12 = 4 + 4 + 4.
```

**Example 2:**

```
Input: n = 13
Output: 2
Explanation: 13 = 4 + 9.
```



### Leetcode

https://leetcode.com/problems/perfect-squares/



### Optimal Solution

Time Complexity: O(N*sqrt(N))

Space Complexity: O(n)

```js
/**
 * @param {number} n
 * @return {number}
 */
var numSquares = function(n) {
    const dp = new Array(n+1).fill(Number.MAX_VALUE);
    dp[0] = 0;
    
    // Here dp is calculated from previous break points
    // i.e dp[5] = dp[4] + 1
    // So the idea is to find the previous perfect square and get the value from it.
    for(let i=1; i<=n; i++) {
        for(let j=1; j*j<=i; j++) {
            dp[i] = Math.min(dp[i], dp[i-j*j] + 1);
        }
    }
    
    return dp[n];
};
```



### Explanation

