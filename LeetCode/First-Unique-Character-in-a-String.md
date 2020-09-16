# First Unique Character in a String

Given a string, find the first non-repeating character in it and return its index. If it doesn't exist, return -1.

**Examples:**

```
s = "leetcode"
return 0.

s = "loveleetcode"
return 2.
```

**Note:** You may assume the string contains only lowercase English letters.



### Leetcode

https://leetcode.com/problems/first-unique-character-in-a-string/



### Optimal Solution

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {string} s
 * @return {number}
 */
var firstUniqChar = function(s) {
  const map = {};
  
  // create a hashMap of chars and count of frequency
  for(const char of s) {
    map[char] = map[char] + 1 || 1;
  }
  
  // iterate over again and check if a character is repeated only once
  for(let i=0; i<s.length; i++) {
    const char = s[i];
    if(map[char] === 1) {
      return i;
    }
  }
  
  return -1;
};
```
