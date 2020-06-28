# Longest Common Prefix

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string `""`.

**Example 1:**

```
Input: ["flower","flow","flight"]
Output: "fl"
```

**Example 2:**

```
Input: ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
```

**Note:**

All given inputs are in lowercase letters `a-z`.



### Leetcode

https://leetcode.com/problems/longest-common-prefix/



### Optimal Solution

Time Complexity:  *O*(*S*) , where S is the sum of all characters in all strings.

Space Complexity: O(1)

```js
/**
 * @param {string[]} strs
 * @return {string}
 */
var longestCommonPrefix = function(strs) {    
    if(strs.length === 0) return "";
    let prefix = strs[0];
    
    for(let i=1; i<strs.length; i++) {
        const string = strs[i];
        // check if the prefix is inside the current string
        // pop prefix from last if there is no prefix found in current string
        // if string.indexOf(prefix) is 0 then we have found a prefix
        while(string.indexOf(prefix) != 0) {
            prefix = prefix.substring(0, prefix.length - 1);
        }
        if(prefix.length === 0) return "";
    }

    return prefix;
};
```

