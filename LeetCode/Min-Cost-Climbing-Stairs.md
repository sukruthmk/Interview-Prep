# Min Cost Climbing Stairs

On a staircase, the `i`-th step has some non-negative cost `cost[i]`assigned (0 indexed).

Once you pay the cost, you can either climb one or two steps. You need to find minimum cost to reach the top of the floor, and you can either start from the step with index 0, or the step with index 1.

**Example 1:**

```
Input: cost = [10, 15, 20]
Output: 15
Explanation: Cheapest is start on cost[1], pay that cost and go to the top.
```



**Example 2:**

```
Input: cost = [1, 100, 1, 1, 1, 100, 1, 1, 100, 1]
Output: 6
Explanation: Cheapest is start on cost[0], and only step on 1s, skipping cost[3].
```



**Note:**

1. `cost` will have a length in the range `[2, 1000]`.
2. Every `cost[i]` will be an integer in the range `[0, 999]`.



### Leetcode

https://leetcode.com/problems/min-cost-climbing-stairs/



### Optimal Solution

Time Complexity: O(N)

Space Complexity: O(N)

```js
/**
 * @param {number[]} cost
 * @return {number}
 */
var minCostClimbingStairs = function(cost) {
  const size = cost.length;
  if(size === 0) return 0;
  
  // initialize dp array
  const dp = new Array(size+1);
  dp[0] = 0;
  dp[1] = cost[0];
  
  for(let i=2; i<=size; i++) {
    dp[i] = Math.min(dp[i-1], dp[i-2]) + cost[i-1]
  }
  
  return Math.min(dp[size], dp[size-1]);
};
```
