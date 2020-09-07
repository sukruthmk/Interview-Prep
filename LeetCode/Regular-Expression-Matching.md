# Regular Expression Matching

Given an input string (`s`) and a pattern (`p`), implement regular expression matching with support for `'.'` and `'*'`.

```
'.' Matches any single character.
'*' Matches zero or more of the preceding element.
```

The matching should cover the **entire** input string (not partial).

**Note:**

- `s` could be empty and contains only lowercase letters `a-z`.
- `p` could be empty and contains only lowercase letters `a-z`, and characters like `.` or `*`.

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
p = "a*"
Output: true
Explanation: '*' means zero or more of the preceding element, 'a'. Therefore, by repeating 'a' once, it becomes "aa".
```

**Example 3:**

```
Input:
s = "ab"
p = ".*"
Output: true
Explanation: ".*" means "zero or more (*) of any character (.)".
```

**Example 4:**

```
Input:
s = "aab"
p = "c*a*b"
Output: true
Explanation: c can be repeated 0 times, a can be repeated 1 time. Therefore, it matches "aab".
```

**Example 5:**

```
Input:
s = "mississippi"
p = "mis*is*p*."
Output: false
```



### Leetcode

https://leetcode.com/problems/regular-expression-matching/



### Optimal Solution

Time Complexity: 

Space Complexity: 

```js
/**
 * @param {string} s
 * @param {string} p
 * @return {boolean}
 */
var isMatch = function(s, p) {
  const pattern = [];
  for(const char of p) {
    // ignore multiple * ex:- a***b -> a*b
    if(char === "*" && pattern[pattern.length-1] === "*") continue;
    pattern.push(char);
  }
  
  const dp = new Array(s.length+1).fill(false).map(() => new Array(pattern.length+1).fill(false));
  dp[0][0] = true;
  
  // deals with pattern like a*, a*b*, a*b*c*
  // these pattern's can match zero or more occurence of characters
  for(let j=1; j<=pattern.length; j++) {
    if(pattern[j-1] === "*") {
      dp[0][j] = dp[0][j-2];
    }
  }
  
  for(let i=1; i<=s.length; i++) {
    for(let j=1; j<=pattern.length; j++) {
      if(s[i-1] === pattern[j-1] || pattern[j-1] === ".") {
        // previous diagonal value
        dp[i][j] = dp[i-1][j-1];
      } else if(pattern[j-1] === "*") {
        if(pattern[j-2] === "." || s[i-1] === pattern[j-2]) {
          // 2 spaces left or top 
          dp[i][j] = dp[i][j-2] || dp[i-1][j];
        } else {
          dp[i][j] = dp[i][j-2];
        }
      }
    }
  }
  
  return dp[s.length][pattern.length];
};
```



### Explanation

https://www.youtube.com/watch?v=l3hda49XcDE