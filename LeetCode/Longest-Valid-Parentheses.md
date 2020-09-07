#  Longest Valid Parentheses

Given a string containing just the characters `'('` and `')'`, find the length of the longest valid (well-formed) parentheses substring.

**Example 1:**

```
Input: "(()"
Output: 2
Explanation: The longest valid parentheses substring is "()"
```

**Example 2:**

```
Input: ")()())"
Output: 4
Explanation: The longest valid parentheses substring is "()()"
```



### Leetcode

https://leetcode.com/problems/longest-valid-parentheses/



### Optimal Solution

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {string} s
 * @return {number}
 */
var longestValidParentheses = function(s) {
  const stack = [];
  let count = 0;
  let max = 0;
  stack.push(-1);
  
  for(let i=0; i<s.length; i++) {
    if(s.charAt(i) === "(") {
      // push the index
      stack.push(i);
    } else {
      stack.pop();
      // stack is empty
      if(stack.length === 0) {
        // push the index
        stack.push(i);
      } else {
        // invalid case
        // get the last valid index and find the substring length
        const subStringLength = i - stack[stack.length - 1];
        max = Math.max(max, subStringLength);
      }
    }
  }
  
  return max;
};
```
