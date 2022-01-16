# Counting Bits
```
4 --> 100
5 --> 101
```

 

**Constraints:**

- `0 <= n <= 105`

 

**Follow up:**

- It is very easy to come up with a solution with a runtime of `O(n log n)`. Can you do it in linear time `O(n)` and possibly in a single pass?
- Can you do it without using any built-in function (i.e., like `__builtin_popcount` in C++)?



### Leetcode

https://leetcode.com/problems/counting-bits/



### Solution

General approach

```js
/**
 * @param {number} n
 * @return {number[]}
 */
var countBits = function(n) {
  const result = []
  
  for(let i=0; i<=n; i++) {
    const binary = Number(i).toString(2);
    const noOfOnes = binary.replace(/0/g, '').length
    result.push(noOfOnes)
  }
  
  return result;
};
```



Using dynamic programming

```js
/**
 * @param {number} n
 * @return {number[]}
 */
var countBits = function(n) {
  const dp = new Array(n+1)
  dp[0] = 0
  dp[1] = 1
  dp[2] = 1
  
  if(n < 3) {
    return dp.slice(0, n+1)
  }
  
  let counter = 2
  
  for(let i=3; i<n+1; i++) {
    if(i === counter*2) {
      counter = counter*2
      dp[i] = 1
    } else {
      dp[i] = dp[counter] + dp[i-counter];
    }
  }
  
  return dp;
};
```

