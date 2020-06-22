# Balanced Brackets

Given a string containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.

Note that an empty string is also considered valid.

**Example 1:**

```
Input: "()"
Output: true
```

**Example 2:**

```
Input: "()[]{}"
Output: true
```

**Example 3:**

```
Input: "(]"
Output: false
```

**Example 4:**

```
Input: "([)]"
Output: false
```

**Example 5:**

```
Input: "{[]}"
Output: true
```

### Leetcode

https://leetcode.com/problems/valid-parentheses/

### Optimal Solution

Time Complexity:

Space Complexity:

```js
/**
 * @param {string} s
 * @return {boolean}
 */

// map of open and closed parentheses
const map = {
  "(": ")",
  "{": "}",
  "[": "]",
}
var isValid = function(s) {
  const stack = [];
  // iterate over all parentheses
  for (let i = 0; i < s.length; i++) {
    const parentheses = s[i];
    // if open push it stack
    if (isOpenParentheses(parentheses)) {
      stack.push(parentheses);
    } else {
      // else pop it from stack and see if the parentheses match
      const open = stack.pop();
      if (!matchParentheses(open, parentheses)) {
        return false;
      }
    }
  }
  // if there are soem unmatched parentheses return false
  if (stack.length > 0) {
    return false;
  }
  return true;
};
// helper function to check if the parentheses is open
const isOpenParentheses = (open) => {
  return map[open];
}
// helper function to match the parentheses
const matchParentheses = (open, closed) => {
  return map[open] === closed;
}
```

