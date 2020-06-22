# Longest Palindromic Substring 

Given a string **s**, find the longest palindromic substring in **s**. You may assume that the maximum length of **s** is 1000.

**Example 1:**

```
Input: "babad"
Output: "bab"
Note: "aba" is also a valid answer.
```

**Example 2:**

```
Input: "cbbd"
Output: "bb"
```

### Leetcode

https://leetcode.com/problems/longest-palindromic-substring/



### Optimal Solution

Time Complexity:

Space Complexity:

```js
/**
 * @param {string} s
 * @return {string}
 */
var longestPalindrome = function(s) {
  let max = "";
  for (let i = 0; i < s.length; i++) {
    // this loop is to take into account 
    // different palindromes like 'aba' and 'abba'
    for (let j = 0; j < 2; j++) {
      let left = i;
      let right = i + j;
      while (s[left] && s[left] === s[right]) {
        left--;
        right++;
      }
      // here imagine we get into string like
      // "sabbad", then
      // right = 5
      // left = 0
      // and actual length of "abba" should be "4"
      // 5 - 0 - 1 === 4
      if ((right - left - 1) > max.length) {
        max = s.substring(left + 1, right);
      }
    }
    // No better move exists
    if (Math.ceil(max.length / 2) >= s.length - i) break;
  }
  return max;
};
```