# Palindrome Check

Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

**Note:** For the purpose of this problem, we define empty string as valid palindrome.

**Example 1:**

```
Input: "A man, a plan, a canal: Panama"
Output: true
```

**Example 2:**

```
Input: "race a car"
Output: false
```

 

**Constraints:**

- `s` consists only of printable ASCII characters.



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

