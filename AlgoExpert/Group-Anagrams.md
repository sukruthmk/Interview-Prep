# Group Anagrams

Given an array of strings, group anagrams together.

**Example:**

```
Input: ["eat", "tea", "tan", "ate", "nat", "bat"],
Output:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]
```

**Note:**

- All inputs will be in lowercase.
- The order of your output does not matter.



### Leetcode

https://leetcode.com/problems/group-anagrams/



### Optimal Solution

Time Complexity: O(NKlogK)

Space Complexity: O(NK)

```js
/**
 * @param {string[]} strs
 * @return {string[][]}
 */
var groupAnagrams = function(strs) {
    const map = {};
    for(const str of strs) {
        const strArr = str.split("");
        strArr.sort();
        const sortedString = strArr.join("")
        if(!map[sortedString]) {
            map[sortedString] = [];
        }
        map[sortedString].push(str);
    }
    return Object.values(map);
};
```

