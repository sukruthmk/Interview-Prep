# Longest Substring Without Repeating Characters

Given a string, find the length of the **longest substring**without repeating characters.

**Example 1:**

```
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 
```

**Example 2:**

```
Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

**Example 3:**

```
Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
             Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```



### Leetcode

https://leetcode.com/problems/longest-substring-without-repeating-characters/



### Optimal Solution

Time Complexity: *O(n)*

Space Complexity: *O(k)* where K is size of set

```js
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function(s) {
    let i=0;
    let j=0;
    let max = 0;
    
    const set = new Set();
    while(j < s.length) {
        if(!set.has(s[j])) {
            set.add(s[j]);
            max = Math.max(max, set.size);
            j++;
        } else {
            set.delete(s[i]);
            i++;
        }
    }
    
    return max;
};
```



### Explanation

https://www.youtube.com/watch?v=3IETreEybaA