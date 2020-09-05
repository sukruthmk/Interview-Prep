# Decode Ways

A message containing letters from `A-Z` is being encoded to numbers using the following mapping:

```
'A' -> 1
'B' -> 2
...
'Z' -> 26
```

Given a **non-empty** string containing only digits, determine the total number of ways to decode it.

**Example 1:**

```
Input: "12"
Output: 2
Explanation: It could be decoded as "AB" (1 2) or "L" (12).
```

**Example 2:**

```
Input: "226"
Output: 3
Explanation: It could be decoded as "BZ" (2 26), "VF" (22 6), or "BBF" (2 2 6).
```



### Leetcode

https://leetcode.com/problems/decode-ways/



### Optimal Solution

##### Approach 1 - backtracking (throws TLE)

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {string} s
 * @return {number}
 */
var numDecodings = function(s) {
  let result = 0;
  
  const backtrack = (s, index) => {
    if(index === s.length) {
      result++;
    }
    for(let i=index; i<s.length; i++) {
      const number = s.substring(index, i+1);
      if(isValidEncoding(number)) {
        backtrack(s, i+1);
      }
    }
  }
  backtrack(s, 0);
  
  return result;
};

const validEncodings = new Set(["1", "2", "3", "4", "5", "6", "7", "8", "9", "10", "11", "12", "13", "14", "15", "16", "17", "18", "19", "20", "21", "22", "23", "24", "25", "26"]);

const isValidEncoding = (number) => {
  return validEncodings.has(number);
}
```



##### Approach 2 - Dynamic Programming

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {string} s
 * @return {number}
 */
var numDecodings = function(s) {
  const dp = new Array(s.length + 1).fill(0);
  dp[0] = 1;
  dp[1] = s[0] === '0' ? 0 : 1;
  
  for(let i=2; i<=s.length; i++) {
    const lastDigit = parseInt(s.substring(i-1, i));
    const lastTwoDigits = parseInt(s.substring(i-2, i));
    if(lastDigit >= 1) {
      dp[i] = dp[i-1];
    }
    if(lastTwoDigits >= 10 && lastTwoDigits <= 26) {
      dp[i] += dp[i-2];
    }
  }
  
  return dp[s.length];
};
```



### Explanation

https://www.youtube.com/watch?v=cQX3yHS0cLo