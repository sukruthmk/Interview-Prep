# Palindrome Check



### Leetcode

https://leetcode.com/problems/valid-palindrome/



### Optimal Solution

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {string} s
 * @return {boolean}
 */
var isPalindrome = function(s) {
  const lowerCaseString = s.toLowerCase();
  const formattedString = lowerCaseString.replace(/[^0-9a-z]/gi, "");
  const stringArr = formattedString.split("");
  return formattedString === stringArr.reverse().join("");
};
```

