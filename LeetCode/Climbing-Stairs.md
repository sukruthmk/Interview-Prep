# Climbing Stairs

You are climbing a stair case. It takes *n* steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

**Example 1:**

```
Input: 2
Output: 2
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps
```

**Example 2:**

```
Input: 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```



### Leetcode

https://leetcode.com/problems/climbing-stairs/



### Optimal Solution

##### Approach 1 - Recursion

Time Complexity: O(2^n)

Space Complexity: O(1)

```js
/**
 * @param {number} n
 * @return {number}
 */
var climbStairs = function(n) {
    let result = 0;
    
    const climb = (totalSteps) => {
        if(totalSteps < 0) {
            return;
        }
        if(totalSteps === 0) {
            result++;
        }
        climb(totalSteps-1);
        climb(totalSteps-2);
    }
    
    climb(n);
    return result;
};
```



##### Approach 2 - Dynamic programming

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {number} n
 * @return {number}
 */
var climbStairs = function(n) {
    if(n === 1) {
        return 1;
    }
    
    const dp = [];
    dp[1] = 1;
    dp[2] = 2;
    
    // using dynamic programming calculate the sum of steps needed for n-1 and n-2.
    for(let i=3; i<=n; i++) {
        dp[i] = dp[i-1] + dp[i-2];
    }
    
    return dp[n];
};
```
