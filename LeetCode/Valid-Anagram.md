# Valid Anagram

Given two strings *s* and *t* , write a function to determine if *t* is an anagram of *s*.

**Example 1:**

```
Input: s = "anagram", t = "nagaram"
Output: true
```

**Example 2:**

```
Input: s = "rat", t = "car"
Output: false
```

**Note:**
You may assume the string contains only lowercase alphabets.

**Follow up:**
What if the inputs contain unicode characters? How would you adapt your solution to such case?



### Leetcode

https://leetcode.com/problems/valid-anagram/



### Optimal Solution

##### Approach 1 - HashMap

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */

var isAnagram = function(s, t) {
  if(s.length != t.length) return false;
  
  const wordMap = {};
  for(const char of s) {
    wordMap[char] = wordMap[char] + 1 || 1;
  }
  
  for(const char of t) {
    if(!wordMap[char]) {
      return false;
    }
    wordMap[char] = wordMap[char] - 1;
  }
  
  return true;
};
```



##### Approach 2 - Sort

Time Complexity: O(nlogn)

Space Complexity: O(nlogn)

```js
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isAnagram = function(s, t) {
  if(s.length != t.length) return false;
  
  // sort both strings in lexicographical manner
  const first = s.split("").sort((a, b) => a.localeCompare(b)).join("");
  const second = t.split("").sort((a, b) => a.localeCompare(b)).join("");
  
  return first == second;
};
```
