# Wildcard Matching

Given an input string (`s`) and a pattern (`p`), implement wildcard pattern matching with support for `'?'` and `'*'`.

```
'?' Matches any single character.
'*' Matches any sequence of characters (including the empty sequence).
```

The matching should cover the **entire** input string (not partial).

**Note:**

- `s` could be empty and contains only lowercase letters `a-z`.
- `p` could be empty and contains only lowercase letters `a-z`, and characters like `?` or `*`.

**Example 1:**

```
Input:
s = "aa"
p = "a"
Output: false
Explanation: "a" does not match the entire string "aa".
```

**Example 2:**

```
Input:
s = "aa"
p = "*"
Output: true
Explanation: '*' matches any sequence.
```

**Example 3:**

```
Input:
s = "cb"
p = "?a"
Output: false
Explanation: '?' matches 'c', but the second letter is 'a', which does not match 'b'.
```

**Example 4:**

```
Input:
s = "adceb"
p = "*a*b"
Output: true
Explanation: The first '*' matches the empty sequence, while the second '*' matches the substring "dce".
```

**Example 5:**

```
Input:
s = "acdcb"
p = "a*c?b"
Output: false
```



### Leetcode

https://leetcode.com/problems/wildcard-matching/



### Optimal Solution

Time Complexity: O(m*n)

Space Complexity: O(m*n)

```js
/**
 * @param {string} s
 * @param {string} p
 * @return {boolean}
 */
var isMatch = function(s, p) {
  let pattern = [];
  
  // replace multiple * with one *
  // ex:- a**b***c -> a*b*c
  for(const char of p) {
    if(char === "*" && pattern[pattern.length - 1] === "*") {
      continue;
    }
    pattern.push(char);
  }
  
  // initialize dp
  const dp = new Array(s.length+1).fill(false).map(() => new Array(pattern.length+1).fill(false));
  dp[0][0] = true;
  if(pattern.length > 0 && pattern[0] === "*") {
    dp[0][1] = true;
  }
  
  for(let i=1; i<dp.length; i++) {
    for(let j=1; j<dp[0].length; j++) {
      // if pattern is ? or pattern equals string i.e a === a
      // then take the diagonal value of dp
      if(pattern[j-1] == "?" || s[i-1] == pattern[j-1]) {
        dp[i][j] = dp[i-1][j-1];
      } else if(pattern[j-1] === "*") { 
        // if pattern is *
        // then take either from top or left
        dp[i][j] = dp[i-1][j] || dp[i][j-1];
      }
    }
  }
  
  return dp[s.length][pattern.length];
};
```



### Explanation

https://www.youtube.com/watch?v=3ZDZ-N0EPV0